# CS2 Cheat - Internal

> Lastest updated£º2024.05.01 10:30

![internal](./internal.png)

## Features

- Bhop

## Download

See [Releases page](https://github.com/yinleiCoder/cs2-cheat-internal/releases) for decorated changelogs. Reading the changelogs is a good way to keep up to date with the things `CS2InternalCheat` has to offer, and maybe will give you ideas of some features that you've been ignoring until now!

## Dll Usage

1. download and install [DirectX 11 SDK](https://www.microsoft.com/en-us/download/details.aspx?id=35)
1. download [ImGui DirectX 11 Kiero Hook.dll](https://github.com/yinleiCoder/cs2-cheat-internal/releases)
1. download [Process Hacker](https://processhacker.sourceforge.io/downloads.php) for windows dll injector
1. inject `ImGui DirectX 11 Kiero Hook.dll` to `cs2.exe` (like Xenos¡¢Process Hacker and so on)

## Local Build

- Change cs2 game **LAUNCH OPTIONS**  with `-insecure` mode
- VisualStudio 2022
	- `Release` and Platform target `x64` because cs2 is a 64-bit game
	- Configuration Properties->General->Configuration Type `Dynamic Library(.dll)`
	- Linker->System->SubSystem `Windows(/SUBSYSTEM:WINDOWS)`
	- Linker->Additional Dependencies `d3d11.lib`
	- Character Set `Use Multi-Byte Character Set`
	- VC++ Directories -> Include Directories. Click on 'Edit' and select the Include folder
located on your DirectX SDK installation path. It is generally this one:
%programfiles(x86)%\Microsoft DirectX SDK (June 2010)\Include\
	- VC++ Directories -> Library Directories. Click on 'Edit' and select the library folder
located on your DirectX SDK installation path. It is generally this one - choose x86 for 32bit and x64 for 64bit:
%programfiles(x86)%\Microsoft DirectX SDK (June 2010)\Lib\
	- VC++ Directories->Include Directories `dependencies/ImGui`[esp]
- Offsets:
	- [offsets](https://github.com/a2x/cs2-dumper/blob/main/output/offsets.hpp)
	- [client.dll](https://github.com/a2x/cs2-dumper/blob/main/output/client.dll.hpp)
	- [buttons](https://github.com/a2x/cs2-dumper/blob/main/output/buttons.hpp)
- Dependencies:
	- [Windows dll injector](https://processhacker.sourceforge.io/) - Process Hacker
	- [ImGui](https://github.com/ocornut/imgui) - Dear ImGui: Bloat-free Graphical User interface for C++ with minimal dependencies
	- [MinHook](https://github.com/TsudaKageyu/minhook) - The Minimalistic x86/x64 API Hooking Library for Windows
	- [source2sdk](https://github.com/neverlosecc/source2sdk/tree/cs2/sdk) - Generated SDK for source2 engine games
- [Microsoft visual key code](https://learn.microsoft.com/en-us/windows/win32/inputdev/virtual-key-codes)
- [Microsoft dlls](https://learn.microsoft.com/zh-cn/windows/win32/dlls/dynamic-link-libraries)
- [unknowncheats](https://www.unknowncheats.me/forum/index.php)
- [guidehacking](https://guidedhacking.com/)

## ESP¡¢Internal¡¢Kernal driver

- [CS2 ESP Cheat](https://github.com/yinleiCoder/cs2-cheat-cpp)
- [CS2 Internal Cheat](https://github.com/yinleiCoder/cs2-cheat-internal)
- [CS2 Kernal Driver Cheat](https://github.com/yinleiCoder/cs2-cheat-kernal-driver)

### What are internals?

When you run a program, it often loads a series of modules in the form of DLL files. DLLs, or dynamic link libraries, are programs that cannot be run directly by double-clicking but instead need to be loaded by an executable program at runtime. Fortunately, we can use this to our advantage with a technique called DLL injection. DLL injection involves forcing a program to load your own library using an injector. When the library is loaded, it operates within the program's virtual memory space. Unlike external cheats, this brings us several benefits. We no longer have to modify memory externally through the Windows API using functions like ReadProcessMemory and WriteProcessMemory; instead, we can simply access the memory directly because our library exists within the program.

