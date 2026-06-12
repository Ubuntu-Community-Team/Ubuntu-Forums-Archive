---
title: "Can't launch terminal"
date: 2022-05-29
forum: General Help
---

### Post by py-ohayo on 2022-05-29
Hello,
I don't know what happened with my system (Ubuntu 18.04), but I can't launch Terminal anymore.
How to remedy this ?
Thanks

---

### Post by tea for one on 2022-05-29
I would first power off and reboot (you know, the old adage, turn it off and turn it on again)

Alternatively, Alt + F2 will open Run a Command, then type [COLOR="#0000FF"]gnome-terminal[/COLOR].

---

### Post by ajgreeny on 2022-05-29
It's impossible to help you without a lot more information.

Please let us know which version of Ubuntu you are using by moving to one of the tty command line terminals with Ctrl+Alt+F1 and run command ***inxi Fzx > inxi.txt***.

This will create a file named **inxi.txt **in your home folder which you can then copy and paste using code tags (see my signature for a How-To) to a reply back here.

---

### Post by py-ohayo on 2022-05-29
Tried it many times.
Doesn't help.
When I try to run gnome-terminal (Alt+F2) I get "Command not found"

---

### Post by py-ohayo on 2022-05-29
Here is my system:
[IMG]https://i.postimg.cc/fT4hHfJT/my-ubuntu-info.png[/IMG]

***inxi Fzx > inxi.txt ***didn't create any file.

---

### Post by py-ohayo on 2022-05-29
Another issue appeared last days:
[IMG]https://i.postimg.cc/k5Vm11FG/ubuntu-update-problem.png[/IMG]

---

### Post by Impavidus on 2022-05-29
> **py-ohayo said:**
> 
When I try to run gnome-terminal (Alt+F2) I get "Command not found"
This means that gnome-terminal isn't installed or the executable has somehow disappeared from its proper location. There are many terminals and gnome-terminal is the default on Ubuntu. Have you any other terminals installed on your system? Maybe xterm works? Otherwise, maybe reinstalling gnome-terminal from the console works:```
sudo apt install --reinstall gnome-terminal
```

> **py-ohayo said:**
> 
***inxi Fzx > inxi.txt ***didn't create any file.
There's an error in that command. It should be```
inxi -Fzx > inxi.txt
```Regardless, even with the error, or even when inxi isn't installed, it would have created the file inxi.txt (although it would have been an empty file). Did you get any error messages?

I'm not sure inxi is installed by default. Maybe you can install it with```
sudo apt install inxi
```

> **py-ohayo said:**
> Another issue appeared last days:
Hard to fix that without a working terminal, but not impossible. It can be hard to reinstall the terminal when your package manager is broken, but maybe it's just a minor issue.

Any idea what you may have done that could have caused this issue? Most issues are caused by the user, some by broken hardware, very few by faulty upgrades.

---

### Post by py-ohayo on 2022-05-29
Thanks for suggestions
I've tried all of them, i.e. reinstalling gnome-terminal, install & run inxi.
I did it using "Enter command" feature (Alt + F2).
Not sure if these command were correctly executed, but finally they didn't help: terminal still doesn't work and there is no inxi.txt file after executing inxi.

---

### Post by tea for one on 2022-05-29
Have you tried to search and install a terminal via Ubuntu Software (or whichever Software Store you have available)?

---

### Post by Impavidus on 2022-05-29
Can you get to the console? ctrl+alt+F1 or one of the other function keys, another one to get you back to the GUI. The exact function key you need depends on the exact version of Ubuntu. Log in with username and password and you'll get a proper shell. Then try to run those commands and report errors you get. Try to use output redirection: command > filename will store the standard output of command in filename, command 2> filename will store standard error in filename.

When using the "enter command" feature, you don't get a full shell, so it may not work.

---

### Post by py-ohayo on 2022-05-29
According to Ubuntu Software the Terminal seems installed:
[IMG]https://i.postimg.cc/nrXxrR5m/terminal-installed.png[/IMG]

---

### Post by py-ohayo on 2022-05-29
> **Impavidus said:**
> Can you get to the console? ctrl+alt+F1 or one of the other function keys, another one to get you back to the GUI. The exact function key you need depends on the exact version of Ubuntu. Log in with username and password and you'll get a proper shell. Then try to run those commands and report errors you get. Try to use output redirection: command > filename will store the standard output of command in filename, command 2> filename will store standard error in filename.

When using the "enter command" feature, you don't get a full shell, so it may not work.

ctrl+alt+F1 has no action on my Ubuntu system (18.04 LTS).

*Log in with username and password and you'll get a proper shell ... *
When I installed Ubuntu, I specified that password isn't asked upon boot/reboot.
Do you mean that if I change reboot with asking password I can access terminal ?

---

### Post by tea for one on 2022-05-29
What happened when you tried to install an alternative terminal via Ubuntu Software?

---

### Post by guiverc on 2022-05-29
Have you altered the default `python3` on your system?

What do you get for `python3 --version`  ?

`gnome-terminal` requires python3; and can refuse to start if the python3 version is changed from the specific version it was intended to work with.

---

### Post by py-ohayo on 2022-05-29
> **guiverc said:**
> Have you altered the default `python3` on your system?

What do you get for `python3 --version`  ?

`gnome-terminal` requires python3; and can refuse to start if the python3 version is changed from the specific version it was intended to work with.

Yes. I installed python 3.10.

---

### Post by py-ohayo on 2022-05-29
> **tea for one said:**
> What happened when you tried to install an alternative terminal via Ubuntu Software?
I can't install it because system says that it's already installed:
[IMG]https://i.postimg.cc/fW131KC3/terminal-installed2.png[/IMG]

---

### Post by tea for one on 2022-05-29
> **py-ohayo said:**
> I can't install it because system says that it's already installed:

I asked if you had tried to install an [COLOR="#0000FF"]alternative[/COLOR] terminal?

Having said that, you probably have xterm installed?
Have you tried to open xterm?

---

### Post by py-ohayo on 2022-05-29
> **tea for one said:**
> I asked if you had tried to install an [COLOR=#0000FF]alternative[/COLOR] terminal?

Having said that, you probably have xterm installed?
Have you tried to open xterm?

Sorry, I misunderstood your question.
Yes, xterm is installed.
I tun inxi in it.
Here is inxi.txt

---

### Post by tea for one on 2022-05-29
Open xterm and enter```
sudo apt-get reinstall gnome-terminal
```
Please post the command and any error messages within code tags.

---

### Post by py-ohayo on 2022-05-29
> **tea for one said:**
> Open xterm and enter```
sudo apt-get reinstall gnome-terminal
```
Please post the command and any error messages within code tags.
Get error:
E: Invalid operation reinstall
BTW how to copy from xterm ?

---

### Post by py-ohayo on 2022-05-29
[FONT=arial]Well ... I proceeded this way:[/FONT]
sudo apt-get remove gnome-terminal && sudo apt-get install gnome-terminal

[FONT=arial]the terminal was indeed reinstalled, but still fails to run.[/FONT]

---

### Post by guiverc on 2022-05-29
> **py-ohayo said:**
> Yes. I installed python 3.10.

If you changed the **default**  python3 to be 3.10; `gnome-terminal` & some other Ubuntu tools that rely on python3 will either fail to work, or potentially worse; work incorrectly (*which can lead to corruption of data*).

Ubuntu 18.04 LTS expects a much older python3; so I'd recommend returning the default back to what it was; ie. reverse your changes that changed the default - if that's what you did.

Yes you can have multiple python3 versions installed; but do not change the default version on a desktop system, or if you want to use Ubuntu tools that use/rely-on `python3`.

---

### Post by tea for one on 2022-05-29
Let's try another approach.
Open xterm and enter ```
gnome-terminal
```
Any error messages?

---

### Post by py-ohayo on 2022-05-29
> **tea for one said:**
> Let's try another approach.
Open xterm and enter ```
gnome-terminal
```
Any error messages?
Here it is (sorry I don't know how to copy from xterm):
[IMG]https://i.postimg.cc/q74g8cHz/terminal-python-issue.png[/IMG]

---

### Post by py-ohayo on 2022-05-29
Well ... I get Terminal working by returning to the previous Python:

[IMG]https://i.postimg.cc/76QgstqB/return-to-old-python.png[/IMG]

Does it mean that I cannot upgrade my Python without perturbing Ubuntu ?

---

### Post by #&amp;thj^% on 2022-05-29
Don't how this happened but I will need to see this, no screenshot please.
```
cat /usr/bin/gnome-terminal > gt.txt
```
my non tainted looks like:
```
#!/usr/bin/python3

import string
import subprocess
import sys
import random

from argparse import ArgumentParser, SUPPRESS
from gi.repository import GLib, Gio


PREFIX = "com.canonical.Terminal."


class GnomeTerminal(object):
    @staticmethod
    def generate_random_string(length=32,
                               chars=string.ascii_lowercase +
                               string.ascii_uppercase):
        return ''.join(random.choice(chars) for _ in range(length))

    @staticmethod
    def find_new_name():
        name = PREFIX + GnomeTerminal.generate_random_string()
        proxy = Gio.DBusProxy.new_for_bus_sync(
            Gio.BusType.SESSION,
            Gio.DBusProxyFlags.DO_NOT_AUTO_START |
            Gio.DBusProxyFlags.DO_NOT_CONNECT_SIGNALS |
            Gio.DBusProxyFlags.DO_NOT_LOAD_PROPERTIES,
            None,
            name,
            "/org/gnome/Terminal",
            "org.freedesktop.Application",
            None)
        return name if proxy.get_name_owner() is None else find_new_name()

    def exit_loop(self, a, b, subprocess):
        sys.exit(subprocess.get_exit_status())

    def server_appeared(self, con, name, owner):
        # start gnome-terminal now
         Gio.Subprocess.new(['/usr/bin/gnome-terminal.real',
                             '--app-id', name] +
                             self.args,
                             Gio.SubprocessFlags.NONE)

    def spawn_terminal_server(self, name, cls):
        args = ['/usr/libexec/gnome-terminal-server',
                '--app-id',
                 name]
        if cls is not None:
            args.extend(['--class', cls])
        ts = Gio.Subprocess.new(args, Gio.SubprocessFlags.NONE)
        ts.wait_async(None, self.exit_loop, ts)

    def __init__(self, args, mainloop):
        self.name = None
        self.mainloop = mainloop

        parser = ArgumentParser(add_help=False,  usage=SUPPRESS)
        parser.add_argument('--app-id', action='store', dest='appid')

        # swallow these arguments
        parser.add_argument('-h', '--help', action='store_true', dest='help')
        parser.add_argument('--disable-factory', action='store_true')
        parser.add_argument('--class', action='store', dest='cls')

        cmdargs, unknown = parser.parse_known_args()

        self.args = unknown
        self.args.insert(0, "/usr/bin/gnome-terminal.real")

        if cmdargs.help:
            self.args.append('--help')

        if cmdargs.cls is not None and cmdargs.appid is None:
            self.name = PREFIX + cmdargs.cls
        elif cmdargs.appid is not None:
            self.name = cmdargs.appid

        # --disable-factory, --class and --app-id weren't supplied, so just
        # invoke g-t
        if not cmdargs.disable_factory and self.name is None:
            sys.exit(subprocess.call(self.args))

        if self.name is None:
            self.name = self.find_new_name()

        Gio.bus_watch_name(Gio.BusType.SESSION,
                           self.name,
                           Gio.BusNameWatcherFlags.NONE,
                           self.server_appeared,
                           None)

        self.spawn_terminal_server(self.name, cmdargs.cls)


def main():
    mainloop = GLib.MainLoop()
    GnomeTerminal(sys.argv[:], mainloop)

    try:
        mainloop.run()
    except KeyboardInterrupt:
        pass


if __name__ == "__main__":
    main()
```
to make it easier for you to copy back here.
are you using any python scripts in your .bashrc file?
**_Never Mind you updated your prefs, I did not see that._**

---

### Post by py-ohayo on 2022-05-29
Here it is.
There is another strange behavior detail that appeared recently: where I click on some program (in favorite bar), other program disappear: for example if Firefox is opened and I click on Terminal in "Favorites", Firefox goes out from the screen

---

### Post by #&amp;thj^% on 2022-05-29
> **py-ohayo said:**
> Here it is.
There is another strange behavior detail that appeared recently: where I click on some program (in favorite bar), other program disappear: for example if Firefox is opened and I click on Terminal in "Favorites", Firefox goes out from the screen

I think i was writing my reply when you added you update-alternatives to use the python3.  I replied back "Never Mind you updated your prefs, I did not see that."
for the other disappearing Icons from favorites, try and remove gnome-terminal from the launcher and re add it, now that it knows which python to use.
My python version is:
```
python3 --version
Python 3.10.4

```
The system very much relies on the correct python for use in the system scripts. IE: updates, and run files, best to leave them alone.

---

### Post by py-ohayo on 2022-05-29
> **1fallen said:**
> I think i was writing my reply when you added you update-alternatives to use the python3.  I replied back "Never Mind you updated your prefs, I did not see that."
for the other disappearing Icons from favorites, try and remove gnome-terminal from the launcher and re add it, now that it knows which python to use.
My python version is:
```
python3 --version
Python 3.10.4

```
The system very much relies on the correct python for use in the system scripts. IE: updates, and run files, best to leave them alone.

If I understood you, if I point once more the python3 to version 3.10, the Terminal will work. Correct ?
Concerning disappeared icons in Favorites, I was misunderstood: all icons are kept in place. It is window that disappears ... I mean that actually only one window can be seen on desktop, i.e. for example I cannot work type something in terminal having Firefox "in background"

---

### Post by #&amp;thj^% on 2022-05-29
> **py-ohayo said:**
> If I understood you, if I point once more the python3 to version 3.10, the Terminal will work. Correct ?


no terminal won't work, This way you can still use the power of 3.10
> **py-ohayo said:**
> 
Concerning disappeared icons in Favorites, I was misunderstood: all icons are kept in place. It is window that disappears ... I mean that actually only one window can be seen on desktop, i.e. for example I cannot work type something in terminal having Firefox "in background"
IJDK, are you sure it's not covered over by the terminal?
Any clues in "dmesg"
```
sudo dmesg | grep firefox
```

---

### Post by dragonfly41 on 2022-05-29
To gather more clues for comparison .. perhaps create a brand new user (guest) account to see if the same issues are seen in a guest user session? Or try LiveUSB "Try Ubuntu" session.

---

### Post by py-ohayo on 2022-05-29
> *no terminal won't work, This way you can still use the power of 3.10.*
So once 3.10 is pointed as python3, I can't use the Terminal anymore. Correct ?

---

### Post by #&amp;thj^% on 2022-05-29
If there is anything different in "**#!/usr/bin/python3"** then the gnome-terminal will fail.
To be clear even if it reads "python3.6" it will fail, or 'python3.10' it will fail.

---

### Post by tea for one on 2022-05-29
> **py-ohayo said:**
>  I mean that actually only one window can be seen on desktop, i.e. for example I cannot work type something in terminal having Firefox "in background"

Have a look at Ubuntu Desktop Guide via Help.
There are a few choices.
Window Switcher  - Super + Tab
Workspaces
Tile Windows - Super + Left Arrow and Super + Right Arrow

---

### Post by py-ohayo on 2022-05-29
> **1fallen said:**
> If there is anything different in "**#!/usr/bin/python3"** then the gnome-terminal will fail.
To be clear even if it reads "python3.6" it will fail, or 'python3.10' it will fail.

The 1st line in gnome-terminal doesn't change - in both cases (3.6.9 and 3.10) it's the same, but when I point python to 3.10, Terminal cannot be run.
How it works on your system ... seems that you told that you use Python 3.10.
So, you don't use gnome-terminal ?

---

### Post by #&amp;thj^% on 2022-05-29
> **py-ohayo said:**
> The 1st line in gnome-terminal doesn't change - in both cases (3.6.9 and 3.10) it's the same, but when I point python to 3.10, Terminal cannot be run.
How it works on your system ... seems that you told that you use Python 3.10.
So, you don't use gnome-terminal ?
I didn't tell it use anything different:
```
apt policy gnome-terminal
gnome-terminal:
  Installed: 3.44.0-1ubuntu1
  Candidate: 3.44.0-1ubuntu1
  Version table:
 *** 3.44.0-1ubuntu1 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status

```
And from your returned gt.txt yours also reads "#!/usr/bin/python3" just python3
On Ubuntu version 18.10 and older, both Python 2 and Python 3 was shipped with the OS. Python 2 can be called by running python in a terminal, while python3 is the alias for Python 3.

On Ubuntu 20.04 onwards, the developers removed and modified the legacy source code so that Python 2 can be removed. Only Python 3 is shipped with the OS out of the box. Because of that, python command now points to Python 3.

Newer versions of popular software acknowledge this change and update their code accordingly, so that the programs does not accidentally run Python 3 code in Python 2.x, which leads to errors. But a lot of them still expect python to be Python 2.x, renders the program unusable on Ubuntu 20.04 and later.

---

### Post by py-ohayo on 2022-05-29
Ok, returning to the original issue, seems that on my Ubuntu 18.04 I can't use **gnome-terminal** if the version 3.10 is pointed as python3. Correct ?

---

### Post by #&amp;thj^% on 2022-05-29
Good grief your still using 18.04, and messed with versions of python installs>>Not Good.
please show me this:
```
apt-cache policy python-is-python3
```

---

### Post by #&amp;thj^% on 2022-05-29
> **py-ohayo said:**
>  I can't use **gnome-terminal** if the version 3.10 is pointed as python3. Correct ?
I don't know how to make that clearer>> **" Correct"**
please read my above post. I need to see this:
```
apt-cache policy python-is-python3
```

---

### Post by py-ohayo on 2022-05-29
```
pavel@ALABAMA:~$ apt-cache policy python-is-python3
N: Unable to locate package python-is-python3
pavel@ALABAMA:~$
```

---

### Post by #&amp;thj^% on 2022-05-29
Can you run update and upgrade in terminal successfully?
IE:
```
sudo apt update
sudo apt upgrade
```
if not what errors are shown

---

### Post by py-ohayo on 2022-05-29
Update:

```
pavel@ALABAMA:~$ sudo apt update
[sudo] password for pavel: 
Hit:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://fr.archive.ubuntu.com/ubuntu bionic InRelease                                                          
Get:3 http://fr.archive.ubuntu.com/ubuntu bionic-updates InRelease [88,7 kB]                                        
Get:4 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  InRelease [1&#8239;581 B]                
Hit:5 https://download.docker.com/linux/ubuntu bionic InRelease                                                     
Get:6 https://nvidia.github.io/libnvidia-container/ubuntu18.04/amd64  InRelease [1&#8239;484 B]                           
Hit:7 http://ppa.launchpad.net/deadsnakes/ppa/ubuntu bionic InRelease                                               
Get:8 http://fr.archive.ubuntu.com/ubuntu bionic-backports InRelease [74,6 kB]                                      
Hit:9 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic InRelease                                         
Get:10 http://security.ubuntu.com/ubuntu bionic-security InRelease [88,7 kB]                                        
Get:11 https://nvidia.github.io/nvidia-container-runtime/ubuntu18.04/amd64  InRelease [1&#8239;481 B]                     
Hit:12 http://ppa.launchpad.net/tomtomtom/k9copy/ubuntu bionic InRelease                                            
Get:13 https://nvidia.github.io/nvidia-docker/ubuntu18.04/amd64  InRelease [1&#8239;474 B] 
Err:4 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A4B469963BF863CC
Get:14 http://fr.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [296 kB]
Get:15 http://fr.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [302 kB]
Get:16 http://fr.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2&#8239;468 B]      
Get:17 http://fr.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [9&#8239;264 B]        
Reading package lists... Done                                                                               
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: GPG error: http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A4B469963BF863CC
E: The repository 'http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
pavel@ALABAMA:~$
```

---

### Post by py-ohayo on 2022-05-29
Upgrade:

```
pavel@ALABAMA:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  distro-info docker-scan-plugin python3-click python3-colorama
The following packages have been kept back:
  cuda-drivers docker-ce u-boot-tools
The following packages will be upgraded:
  apt apt-transport-https apt-utils base-files cmake cmake-data command-not-found command-not-found-data containerd.io deja-dup dirmngr docker-ce-cli friendly-recovery fwupd fwupd-signed gdb gdbserver
  gir1.2-mutter-2 gir1.2-snapd-1 gnome-shell gnome-shell-common gnupg gnupg-agent gnupg-l10n gnupg-utils gpg gpg-agent gpg-wks-client gpg-wks-server gpgconf gpgsm gpgv initramfs-tools
  initramfs-tools-bin initramfs-tools-core iproute2 libappindicator3-1 libapt-inst2.0 libapt-pkg5.0 libasound2 libasound2-data libasound2-dev libaudit-common libaudit1 libc-bin libc-dev-bin libc6
  libc6:i386 libc6-dbg libc6-dev libc6-i386 libcryptsetup12 libfwupd2 libgnutls30 libkeyutils1 libmutter-2-0 libnetplan0 libnss-myhostname libnss-systemd libnvidia-container-tools libnvidia-container1
  libpam-modules libpam-modules-bin libpam-runtime libpam-systemd libpam0g libpam0g-dev libsnapd-glib1 libsystemd0 libudev1 libwhoopsie0 libxnvctrl0 linux-base linux-firmware locales lshw
  multiarch-support mutter mutter-common netplan.io nplan nvidia-container-toolkit nvidia-modprobe nvidia-prime nvidia-settings openssh-client python-apt-common python3-apt python3-commandnotfound
  python3-distupgrade python3-httplib2 python3-software-properties python3-tornado sbsigntool software-properties-common software-properties-gtk systemd systemd-sysv ubuntu-advantage-tools
  ubuntu-drivers-common ubuntu-keyring ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk udev ufw update-notifier update-notifier-common whoopsie
108 upgraded, 4 newly installed, 0 to remove and 3 not upgraded.
Need to get 94,8 MB/199 MB of archives.
After this operation, 6&#8239;993 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://fr.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libc6-dbg amd64 2.27-3ubuntu1.6 [5&#8239;162 kB]
Get:2 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  libxnvctrl0 510.47.03-0ubuntu1 [20,5 kB]                
Err:2 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  libxnvctrl0 510.47.03-0ubuntu1                                 
  File has unexpected size (20490 != 20486). Mirror sync in progress? [IP: 152.199.20.126 80]
  Hashes of expected file:
   - SHA512:918d2057ea02f3ccf6f9efa255593bbe24bfe58ed2714e64898749ca86a3d0a6c7feead38648163baaf749711273633cb8d5acef623cbfb820661ec374ddff45
   - SHA256:ffa61c3dfb479abc67e2019b906d718144d7130b784bd0be6ed08b71c4820605
   - SHA1:aeed1ebfb5d81f7fbba106a76a6383f19e859467 [weak]
   - MD5Sum:467a48c22b5f5a8be81e3e8981107d10 [weak]
   - Filesize:20486 [weak]
Get:3 https://download.docker.com/linux/ubuntu bionic/stable amd64 containerd.io amd64 1.6.4-1 [28,1 MB]                                        
Get:4 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  nvidia-settings 510.47.03-0ubuntu1 [894 kB]
Err:4 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  nvidia-settings 510.47.03-0ubuntu1
  File has unexpected size (893670 != 893668). Mirror sync in progress? [IP: 152.199.20.126 80]
  Hashes of expected file:
   - SHA512:c54667544235f3342527d1192c8899343cfae1b942394078cda60881bcd17b5927020b85279bd3c68ad4939e1738e08c6c3346d3f7be98ade1d72007df040e43
   - SHA256:ff5e5d25fa3c4e1b40768352b35bd392cc68bd95fedfb6961465be8a3ef46f6a
   - SHA1:082254299c70f2224ddffaa3cca4506e4e8b2f07 [weak]
   - MD5Sum:eba37f44334d0788f30b135f06ca7fea [weak]
   - Filesize:893668 [weak]
Get:5 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  nvidia-modprobe 510.47.03-0ubuntu1 [19,8 kB]              
Err:5 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  nvidia-modprobe 510.47.03-0ubuntu1                        
  File has unexpected size (19802 != 19798). Mirror sync in progress? [IP: 152.199.20.126 80]
  Hashes of expected file:
   - SHA512:cc56f27f06d636626d70976c36d8d064990d7d6d7e17f3a8533ed86849fb43acf19c9b38a349667e55dd01e144637f0ea8bcfffabb33b280fd7c9935440ce616
   - SHA256:f26231377ac0f250e9718609f0e360399991f16a5a45131e205b41bf5d16778a
   - SHA1:af5569467c9298cfe0bb1a69b6608e8a872077dd [weak]
   - MD5Sum:ec74f11420daeb0442d266792bff29fc [weak]
   - Filesize:19798 [weak]
Get:6 http://fr.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libc6-i386 amd64 2.27-3ubuntu1.6 [2&#8239;651 kB]
Get:7 http://fr.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libc-dev-bin amd64 2.27-3ubuntu1.6 [71,9 kB]
Get:8 http://fr.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libc6-dev amd64 2.27-3ubuntu1.6 [2&#8239;587 kB]
Get:9 http://fr.archive.ubuntu.com/ubuntu bionic-updates/main i386 libc6 i386 2.27-3ubuntu1.6 [2&#8239;555 kB]
Get:10 http://fr.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libc6 amd64 2.27-3ubuntu1.6 [2&#8239;831 kB]
Get:11 http://fr.archive.ubuntu.com/ubuntu bionic-updates/main amd64 locales all 2.27-3ubuntu1.6 [3&#8239;613 kB]
Get:12 http://fr.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libc-bin amd64 2.27-3ubuntu1.6 [640 kB]
Get:13 http://fr.archive.ubuntu.com/ubuntu bionic-updates/main amd64 ubuntu-drivers-common amd64 1:0.8.6.3~0.18.04.2 [52,6 kB]
Get:14 http://fr.archive.ubuntu.com/ubuntu bionic/main amd64 python3-colorama all 0.3.7-1 [14,9 kB]
Get:15 http://fr.archive.ubuntu.com/ubuntu bionic/main amd64 python3-click all 6.7-3 [56,5 kB]
Get:16 http://fr.archive.ubuntu.com/ubuntu bionic-updates/main amd64 distro-info amd64 0.18ubuntu0.18.04.1 [19,9 kB]
Get:17 http://fr.archive.ubuntu.com/ubuntu bionic-updates/main amd64 ubuntu-advantage-tools amd64 27.8~18.04.1 [717 kB]
Get:18 http://fr.archive.ubuntu.com/ubuntu bionic-updates/main amd64 multiarch-support amd64 2.27-3ubuntu1.6 [6&#8239;960 B]
Get:19 http://fr.archive.ubuntu.com/ubuntu bionic-updates/main amd64 openssh-client amd64 1:7.6p1-4ubuntu0.7 [610 kB]
Get:20 http://fr.archive.ubuntu.com/ubuntu bionic-updates/main amd64 sbsigntool amd64 0.9.2-2ubuntu1~18.04.2 [62,5 kB]
Get:21 https://download.docker.com/linux/ubuntu bionic/stable amd64 docker-ce-cli amd64 5:20.10.16~3-0~ubuntu-bionic [40,6 MB]                                                                            
Get:22 https://download.docker.com/linux/ubuntu bionic/stable amd64 docker-scan-plugin amd64 0.17.0~ubuntu-bionic [3&#8239;521 kB]                                                                              
Fetched 93,9 MB in 15s (6&#8239;202 kB/s)                                                                                                                                                                       
E: Failed to fetch http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/./libxnvctrl0_510.47.03-0ubuntu1_amd64.deb  File has unexpected size (20490 != 20486). Mirror sync in progress? [IP: 152.199.20.126 80]
   Hashes of expected file:
    - SHA512:918d2057ea02f3ccf6f9efa255593bbe24bfe58ed2714e64898749ca86a3d0a6c7feead38648163baaf749711273633cb8d5acef623cbfb820661ec374ddff45
    - SHA256:ffa61c3dfb479abc67e2019b906d718144d7130b784bd0be6ed08b71c4820605
    - SHA1:aeed1ebfb5d81f7fbba106a76a6383f19e859467 [weak]
    - MD5Sum:467a48c22b5f5a8be81e3e8981107d10 [weak]
    - Filesize:20486 [weak]
E: Failed to fetch http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/./nvidia-settings_510.47.03-0ubuntu1_amd64.deb  File has unexpected size (893670 != 893668). Mirror sync in progress? [IP: 152.199.20.126 80]
   Hashes of expected file:
    - SHA512:c54667544235f3342527d1192c8899343cfae1b942394078cda60881bcd17b5927020b85279bd3c68ad4939e1738e08c6c3346d3f7be98ade1d72007df040e43
    - SHA256:ff5e5d25fa3c4e1b40768352b35bd392cc68bd95fedfb6961465be8a3ef46f6a
    - SHA1:082254299c70f2224ddffaa3cca4506e4e8b2f07 [weak]
    - MD5Sum:eba37f44334d0788f30b135f06ca7fea [weak]
    - Filesize:893668 [weak]
E: Failed to fetch http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/./nvidia-modprobe_510.47.03-0ubuntu1_amd64.deb  File has unexpected size (19802 != 19798). Mirror sync in progress? [IP: 152.199.20.126 80]
   Hashes of expected file:
    - SHA512:cc56f27f06d636626d70976c36d8d064990d7d6d7e17f3a8533ed86849fb43acf19c9b38a349667e55dd01e144637f0ea8bcfffabb33b280fd7c9935440ce616
    - SHA256:f26231377ac0f250e9718609f0e360399991f16a5a45131e205b41bf5d16778a
    - SHA1:af5569467c9298cfe0bb1a69b6608e8a872077dd [weak]
    - MD5Sum:ec74f11420daeb0442d266792bff29fc [weak]
    - Filesize:19798 [weak]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
pavel@ALABAMA:~$
```

---

### Post by #&amp;thj^% on 2022-05-29
Mostly all warnings, except this one : "E: The repository 'http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64 InRelease' is no longer signed."
We'll work on that later.
What about the second one
```
sudo apt upgrade
```
Ok I just seen that as well.
run:
```
sudo apt-get --fix-missing
```

---

### Post by DuckHook on 2022-05-29
@OP

To preserve formatting and veracity, please use [noparse]```

```[/noparse] tags when posting output. Also, use only standard fonts and styles. Unusual fonts/colours/styles make your output difficult to read, especially on small screens.

---

### Post by py-ohayo on 2022-05-30
> sudo apt-get --fix-missing

[FONT=arial]It seems that it requires a command (e.g. update ?). In this form this instruction do nothing[/FONT]

---

### Post by ajgreeny on 2022-05-30
Yes, try
**sudo apt install --fix-missing**

---

### Post by py-ohayo on 2022-05-30
```
pavel@ALABAMA:~$ sudo apt install --fix-missing
[sudo] password for pavel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 111 not upgraded.
pavel@ALABAMA:~$
```

---

### Post by #&amp;thj^% on 2022-05-30
First get rid of the bad Cuda Repo from your source list.
then run:
```
sudo apt clean
```
and:
```
sudo apt autoremove
```
If you really need the Cuda repo use:
```
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/cuda-repo-ubuntu1804_10.0.130-1_amd64.deb
sudo dpkg -i cuda-repo-ubuntu1804_10.0.130-1_amd64.deb
sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub
sudo apt-get update
```

---

### Post by mIk3_08 on 2022-05-31
This thread is very useful. If this thread is done and I think it found a solution to the issue it is best if we mark this as solve so that other new users in this forum that may encounter same issue as this and might scanned this thread may help them solve their issues. For more details on how to mark solve the issue just click solve issue below. Regards and cheers.

---

### Post by py-ohayo on 2022-09-18
Finally, at the time this thread was started (end of May), I could run the **terminal** (I don't remember how the problem was resolved)
Recently I updated Ubuntu to 20.04. Then I updated Python to 3.10.
The first two days, everything was fine. But yesterday I discovered that **terminal** as well as some other programs (Software & updates, software Updates) were not working.
Tried with 2 versions of python3 - 3.6 (which was installed with Ubuntu) and 3.10(that I installed) - doesn't work in 2 cases.
Any suggestions?

---

### Post by Impavidus on 2022-09-18
I haven't read this entire thread. Maybe this was mentioned already.

Ubuntu 20.04 comes with Python 3.8. Changing the default version of Python on your system (for example to 3.10) will break it. If you want Python 3.10, either isolate it from the rest of your system or run Ubuntu 22.04.

---

### Post by py-ohayo on 2022-09-18
Well, the solution seems to be found (found here [https://www.maketecheasier.com/fix-ubuntu-cannot-open-terminal/](https://www.maketecheasier.com/fix-ubuntu-cannot-open-terminal/)) ... but not sure that it is the best one:[COLOR=#666666][/COLOR]I change[COLOR=#666666][/COLOR]d[COLOR=#666666][I]
#!/usr/bin/python3[/I][/COLOR]
to[COLOR=#666666][I]
#!/usr/bin/python3.8[/I][/COLOR]
in[COLOR=#000000][B]
/[/B][/COLOR]usr[COLOR=#000000]**/**[/COLOR]bin[COLOR=#000000]**/**[/COLOR]gnome-terminal
Actually I still don't understand how to manage correctly this python3 staff.
The version 3.8 was probably installed when I installed IDLE environment for python ... because when launching IDLE it info that python 3.8 is used.
When installing IDLE I didn't specify the version expecting the last one.
Apparently there is no IDLE for python 3.10.
What is strange is that this python 3.8 does not appear in the list of python3 alternatives:

pavel@ALABAMA:~$ update-alternatives --list python3
/usr/bin/python3.10
/usr/bin/python3.6

Any suggestions concerning these python3 issues ?
Thanks.

---

### Post by py-ohayo on 2022-09-18
Thanks !
So python 3.8 didn't come with IDLE, but when upgrading Ubuntu...and 3.6 remained from my previous 18.04.
So, probably I can remove 3.6 and change link here

pavel@ALABAMA:/etc/alternatives$ ls python3* -l
lrwxrwxrwx 1 root root 18 sept. 18 11:50 python3 -> /usr/bin/python3.6

By the way, as I remember, when I run do-release-upgrade, I was proposed 20.04, but not 22.04.
Does it mean that 22.04 can be upgraded _only_ over 20.04 ?

---

### Post by Impavidus on 2022-09-18
I just skimmed through the first few pages of this thread and it appears you made the same error as when you first started it.
> **py-ohayo said:**
> Well, the solution seems to be found (found here [https://www.maketecheasier.com/fix-ubuntu-cannot-open-terminal/](https://www.maketecheasier.com/fix-ubuntu-cannot-open-terminal/)) ... but not sure that it is the best one:I changed[COLOR=#666666][I]
#!/usr/bin/python3[/I][/COLOR]
to[COLOR=#666666][I]
#!/usr/bin/python3.8[/I][/COLOR]
in[COLOR=#000000][B]
/[/B][/COLOR]usr[COLOR=#000000]**/**[/COLOR]bin[COLOR=#000000]**/**[/COLOR]gnome-terminalWell, it's a solution, but not very good. This fixes gnome-terminal, but not the other applications that may have broken. If this solution works, Python 3.8 must still be installed. It's just not the default. I don't know how you installed 3.10, but you have to find a way to make sure the default points to 3.8, not 3.10.

Many core components of Ubuntu depend on Python and they all want one specific version, so don't touch that. It's not very elegant. Python is not so good at backward compatibility. I've never had to install an alternative Python version myself, but it's possible. Somebody here will know how.
> **py-ohayo said:**
> 
By the way, as I remember, when I run do-release-upgrade, I was proposed 20.04, but not 22.04.
Does it mean that 22.04 can be upgraded _only_ over 20.04 ?
Ubuntu 18.04 offers an upgrade to 20.04, 20.04 to 22.04. You can't skip it. Well, you can, if you really wish, but it's an unsupported hack and more likely to result in failure.

Ubuntu 22.04 comes with Python 3.10. It also has idle for that Python version in the repos, just as 20.04 has idle for Python 3.8 in the repos.

---

