# vmulti

Virtual Multiple HID Driver (multitouch, mouse, digitizer, keyboard, joystick)

### About this fork

Relative mouse mode has been removed to try to keep away people who want to use signed versions of this driver to write software that compromises the competitive integrity of online games. If they do that, it causes problems for people using signed versions of this driver for its intended purposes. If you make that kind of software, please, I implore you, use stolen certs or [commercially-signed drivers](https://github.com/X9VoiD/vmulti-bin/releases/tag/v1.0) instead! (The signed drivers in that link come from a commercial hardware manufacturer, not an open-source project.)

Digitizer mode has been dramatically overhauled to support every feature that graphics tablets actually use.

### Prerequisites

Visual Studio 2022 Community Edition + "Desktop development with C/C++" toolchain via Visual Studio Installer

Might also need the "Windows Driver Kit" from Visual Studio Installer

### Building

Open the .sln in Visual Studio 2022. Open sys/vmulti.c and read the comments at the top. Follow the instructions in those comments, building the vmulti project twice.

### Installing

On 64-bit Windows, this requires first rebooting windows with Test Mode enabled so that test-signed drivers can be loaded.

Copy devcon.exe, DIFxAPI.dll, DIFxCmd.exe, and maybe WdfCoInstaller01009.dll to for_testing.

Run install_hiddriver.bat in for_testing.

### Uninstalling

Run remove_hiddriver.bat in for_testing.

If it fails do this: Open up a command prompt as Administrator and run `pnputil /enum-drivers`. Look for drivers with an Original Name of `vmulti.inf` and note their Published Name. Run `pnputil /delete-driver XXXX.inf /uninstall` for the Published Name of those drivers, one at a time. Go into Device Manager and look under "Other Devices" for "VMulti HID" devices. If there are any, right click and uninstall them.

### Testing

Run testvmulti.exe /multitouch to move the cursor via virtual multitouch
Run testvmulti.exe /mouse to move the cursor via virtual mouse
Run testvmulti.exe /digitizer to move the cursor via virtual digitizer 
