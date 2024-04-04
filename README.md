# Informations

This template has been setup on a Macbook Pro M1, if you want to run it on Windows or Linux you will have to modify some configuration in *tasks.json*, *launch.json* and *c_cpp_properties.json* files located in the *.vscode* folder.

# Requirements

- Install **DevkitPro** on your system and add it to your PATH.
- Install **mGBA** emulator (I use version **0.10.3**) and add it to your Applications folder (you can use another emulator but you'll have to change the configuration in .vscode/launch.json)
- Obviously you'll need **VSCode**

# Good to know

If you cannot debug your program because of some failures when connecting to the GDB server, you may have to perform a codesign for GDB (I think this issue only occurs on MacOS).
To do so, you can follow [this guide](https://medium.com/@royalstream/how-to-install-and-codesign-gdb-on-os-x-el-capitan-aab3d1172e95), just skip the first step about installing GDB (you'll use the one provided in devkitpro), and replace the gdb path in the **codesign** command with the devkitpro gdb path:

```shell
# replace :
codesign -s gdb-cert /usr/local/bin/gdb
# with :
codesign -s gdb-cert /opt/devkitpro/devkitARM/bin/arm-none-eabi-gdb
```

# Usage

- First you need to compile your code by running the "Make" task. (cmd + shift + P > Run Task > Make)
- Then open the Debug Tab, select **(gdb) Launch** and click the green arrow.

If everything works your program should start in the mGBA emulator, and if you placed breakpoints in VSCode, they should be triggered in VSCode.