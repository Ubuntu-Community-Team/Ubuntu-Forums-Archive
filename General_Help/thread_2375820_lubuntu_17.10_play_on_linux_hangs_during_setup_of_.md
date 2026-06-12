---
title: "lubuntu 17.10 play on linux hangs during setup of game"
date: 2017-10-27
forum: General Help
---

### Post by cdoublejj on 2017-10-27
it's been hanging for several hours now. it is stuck at please wait while "virtual drive is being created"

here is the log

[PHP]PlayOnLinux debugging tool (v4.2.12)
-----------------------------------------------
Debugging: GOG.com - Darkstone

Warning: This is a PlayOnLinux script logfile. It does not contain everything that happened in your program\'s virtual drive (wineprefix)
Please do not use this logfile on winehq forum, this logfile is not interesting for wine debugging.

Date: 10/27/17 07:47:02

> uname -a
  Linux LubuntuCore2haf 4.13.0-16-generic #19-Ubuntu SMP Wed Oct 11 18:35:14 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
> lsb_release -a
  
> wine --version (Be careful; this version might not be the version used
in the script. Read the content of this file for more information)
  wine-2.19 (Staging)
> glxinfo \| grep rendering
  direct rendering: Yes
    GL_NV_path_rendering, GL_NV_pixel_data_range, GL_NV_point_sprite, 
    GL_NV_path_rendering, GL_NV_pixel_data_range, GL_NV_point_sprite, 
    GL_NV_packed_float_linear, GL_NV_path_rendering, 
> glxinfo \| grep renderer
  OpenGL renderer string: GeForce GTX 770/PCIe/SSE2
> OpenGL libs
  check_dd_x86 missing, test skipped
  check_dd_amd64 missing, test skipped
> export
  declare -x AMD64_COMPATIBLE="True"
declare -x APPLICATION_TITLE="PlayOnLinux"
declare -x DBUS_SESSION_BUS_ADDRESS="unix:path=/run/user/1000/bus"
declare -x DEBIAN_PACKAGE="TRUE"
declare -x DEFAULTS_PATH="/usr/share/gconf/Lubuntu.default.path"
declare -x DESKTOP="/home/user/Desktop"
declare -x DESKTOP_SESSION="Lubuntu"
declare -x DISPLAY=":0.0"
declare -x DONT_MONITOR="1"
declare -x DYLDPATH_ORIGIN=""
declare -x DYLD_LIBRARY_PATH=""
declare -x GDMSESSION="Lubuntu"
declare -x GDM_LANG="en_US"
declare -x GECKO_SITE="http://wine.playonlinux.com/gecko"
declare -x GIO_LAUNCHED_DESKTOP_FILE="/usr/share/applications/PlayOnLinux.desktop"
declare -x GIO_LAUNCHED_DESKTOP_FILE_PID="10707"
declare -x GNUPGHOME="/home/user/.PlayOnLinux//gpg"
declare -x GTK_OVERLAY_SCROLLING="0"
declare -x G_FILENAME_ENCODING="UTF-8"
declare -x HOME="/home/user"
declare -x IGNORE_ICON_DIR="false"
declare -x LANG="en_US.UTF-8"
declare -x LANGUAGE="en_US"
declare -x LD_32_PATH_ORIGIN=""
declare -x LD_LIBRARY_PATH=""
declare -x LD_PATH_ORIGIN=""
declare -x LOGNAME="user"
declare -x MACHTYPE="x86_64-pc-linux-gnu"
declare -x MANDATORY_PATH="/usr/share/gconf/Lubuntu.mandatory.path"
declare -x MD5_COMMAND="md5sum"
declare -x MONO_SITE="http://wine.playonlinux.com/mono"
declare -x OLDPWD="/home/user/.PlayOnLinux/configurations/setups/GOG.com - Darkstone"
declare -x OS_NAME="linux"
declare -x OpenGL32="1"
declare -x OpenGL64="1"
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin"
declare -x PATH_ORIGIN="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin"
declare -x PLAYONLINUX="/usr/share/playonlinux"
declare -x POL_ARCH="x86"
declare -x POL_COOKIE="okZGbz5ntOLjKa07pBU7"
declare -x POL_CURL="curl"
declare -x POL_DNS="playonlinux.com"
declare -x POL_HOST="127.0.0.1"
declare -x POL_ID="72419074"
declare -x POL_LANG="en"
declare -x POL_OS="Linux"
declare -x POL_PORT="30001"
declare -x POL_PYTHON="python"
declare -x POL_SetupWindow_ID="12105"
declare -x POL_TERM="x-terminal-emulator"
declare -x POL_UPTODATE="TRUE"
declare -x POL_USER_ARCH="x86"
declare -x POL_USER_ROOT="/home/user/.PlayOnLinux/"
declare -x POL_WGET="env LD_LIBRARY_PATH=\"\" wget --prefer-family=IPv4 -q"
declare -x PWD="/usr/share/playonlinux/python"
declare -x QT_ACCESSIBILITY="1"
declare -x QT_PLATFORM_PLUGIN="lxqt"
declare -x QT_QPA_PLATFORMTHEME="lxqt"
declare -x QT_STYLE_OVERRIDE="gtk"
declare -x REPERTOIRE="/home/user/.PlayOnLinux/"
declare -x SCRIPTID="GOG.com - Darkstone"
declare -x SED="sed"
declare -x SETUPWINDOW_INIT="true"
declare -x SHELL="/bin/bash"
declare -x SHLVL="3"
declare -x SITE="http://repository.playonlinux.com"
declare -x SSH_AGENT_PID="892"
declare -x SSH_AUTH_SOCK="/tmp/ssh-gtD0X4xz1cT7/agent.840"
declare -x TEXTDOMAIN="pol"
declare -x TITLE="GOG.com - Darkstone"
declare -x TITRE="PlayOnLinux"
declare -x UBUNTU_MENUPROXY="0"
declare -x USER="user"
declare -x VERSION="4.2.12"
declare -x WGETRC="/home/user/.PlayOnLinux//configurations/wgetrc"
declare -x WINEDLLOVERRIDES="winemenubuilder.exe=d"
declare -x WINEPREFIX="/home/user/.PlayOnLinux//wineprefix/default"
declare -x WINE_SITE="http://wine.playonlinux.com/binaries"
declare -x WorkingDirectory="/home/user"
declare -x XAUTHORITY="/home/user/.Xauthority"
declare -x XDG_CONFIG_DIRS="/etc/xdg/lubuntu:/etc/xdg/xdg-Lubuntu:/etc/xdg"
declare -x XDG_CONFIG_HOME="/home/user/.config"
declare -x XDG_CURRENT_DESKTOP="LXDE"
declare -x XDG_DATA_DIRS="/etc/xdg/lubuntu:/usr/share/gdm:/var/lib/menu-xdg:/usr/share/Lubuntu:/usr/local/share:/usr/share:/var/lib/snapd/desktop"
declare -x XDG_GREETER_DATA_DIR="/var/lib/lightdm-data/user"
declare -x XDG_MENU_PREFIX="lxde-"
declare -x XDG_RUNTIME_DIR="/run/user/1000"
declare -x XDG_SEAT="seat0"
declare -x XDG_SEAT_PATH="/org/freedesktop/DisplayManager/Seat0"
declare -x XDG_SESSION_DESKTOP="Lubuntu"
declare -x XDG_SESSION_ID="c1"
declare -x XDG_SESSION_PATH="/org/freedesktop/DisplayManager/Session0"
declare -x XDG_SESSION_TYPE="x11"
declare -x XDG_VTNR="7"
declare -x _LXSESSION_PID="840"


10/27/17 07:47:08 - [POL_Call] Message: Calling POL_GoG_setup
10/27/17 07:47:08 - [POL_Call] Message: ----- Starting function POL_GoG_setup -----
10/27/17 07:47:08 - [POL_GPG_auth_script] Message: Checking signature of POL_GoG_setup
10/27/17 07:47:08 - [POL_GPG_install_key] Message: Importing PlayOnLinux public key
10/27/17 07:47:08 - [POL_Source] Message: POL GPG : Good signature
10/27/17 07:47:08 - [source] Message: PlayOnLinux can understand GoG_Download
10/27/17 07:47:11 - [POL_SetupWindow_icon_menu] Message: icon_menu answer: Use a setup file in my computer
10/27/17 07:47:11 - [POL_SetupWindow_InstallMethod] Message: Install method: LOCAL
10/27/17 07:47:11 - [source] Message: Install method LOCAL
10/27/17 07:47:17 - [POL_SetupWindow_browse] Message: browser answer: /home/user/Downloads/setup_darkstone_2.0.0.10.exe
10/27/17 07:47:17 - [POL_Call] Message: ----- Ending function POL_GoG_setup -----
10/27/17 07:47:17 - [POL_Wine_SelectPrefix] Message: Selecting prefix: Darkstone_gog
10/27/17 07:47:17 - [POL_Wine_PrefixCreate] Message: Setting POL_WINEVERSION to 1.6.1
10/27/17 07:47:17 - [POL_Wine_PrefixCreate] Message: Creating prefix (1.6.1)...
10/27/17 07:47:17 - [POL_Wine_PrefixCreate] Message: Using wine 1.6.1
10/27/17 07:47:17 - [POL_Wine_InstallVersion] Message: Installing wine version path: 1.6.1, x86
10/27/17 07:59:23 - [POL_Wine_Install_resources] Message: Installing gecko for wine 1.6.1 x86
10/27/17 07:59:23 - [POL_Wine_Install_resources] Message: Linking gecko
10/27/17 07:59:23 - [POL_Wine_Install_resources] Message: Installing wine_gecko-2.24-x86.msi
10/27/17 07:59:23 - [POL_Download] Message: Downloading http://wine.playonlinux.com/gecko/x86/wine_gecko-2.24-x86.msi
10/27/17 07:59:34 - [POL_Download] Message: Download MD5 matches
10/27/17 07:59:34 - [POL_Wine_Install_resources] Message: Installing mono for wine 1.6.1 x86
10/27/17 07:59:34 - [POL_Wine_Install_resources] Message: Linking mono
10/27/17 07:59:34 - [POL_Wine_Install_resources] Message: Installing wine-mono-0.0.8.msi
10/27/17 07:59:34 - [POL_Download] Message: Downloading http://wine.playonlinux.com/mono/wine-mono-0.0.8.msi
10/27/17 07:59:58 - [POL_Download] Message: Download MD5 matches
10/27/17 07:59:58 - [POL_Config_PrefixWrite] Message: Prefix config write: ARCH x86
10/27/17 07:59:58 - [POL_Config_PrefixWrite] Message: Prefix config write: VERSION 1.6.1
10/27/17 07:59:58 - [POL_Wine] Message: Running wine-1.6.1 --version (Working directory : /home/user/.PlayOnLinux/wine/mono)
10/27/17 07:59:58 - [POL_Wine] Message: Notice: PlayOnLinux deliberately disables winemenubuilder. See http://www.playonlinux.com/fr/page-26-Winemenubuilder.html
wine-1.6.1
10/27/17 07:59:58 - [POL_Wine] Message: Wine return: 0

[/PHP]

---

### Post by 441fp on 2018-03-09
i have the same problem trying to install adobe digital editions 4.5 (ubuntu 17.10)

have someone any solution?

thx franz

---

