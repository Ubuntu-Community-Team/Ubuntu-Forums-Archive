---
title: "Installing LeJOS 0.6 for MindStorms on 8.04"
date: 2008-07-09
forum: General Help
---

### Post by VancouverCowboy on 2008-07-09
For the benefit of anyone running Hardy Heron who wants to use leJOS, I've summarized the steps (minus my errors and back-tracking!) to install and configure leJOS to work on my Ubuntu laptop with Bluetooth.

I run Ubuntu 8.04 fully updated on a new HP Pavilion DV9744CA latop with a D-Link DBT-120 Bluetooth Dongle.
[list]
1.  Install these development packages:

[b][list]sudo apt-get install libusb-dev
sudo apt-get install libbluetooth-dev
sudo apt-get install gcj[/list][/b]

2.  Use Synaptic Package Manager to install NetBeans if you want to use NetBeans--I happen to prefer it but it's a personal choice

3.  NetBeans is installed with the openjdk Java Development Kit.  The leJOS development team forum recommends using the Sun Java 1.6 SDK which can also be downloaded with Synaptic

4.  If you download the Sun Java 1.6 SDK, edit the NetBeans launcher to include **--jdkhome /usr/lib/jvm/java-6-sun-1.6.0.06** so that it uses the Java Sun version and not the openjdk

5.  You will also have to choose which version you will use: **sudo update-alternatives - - config java** (I found that here [http://forum.java.sun.com/thread.jspa?threadID=5191319&messageID=9756412](http://forum.java.sun.com/thread.jspa?threadID=5191319&messageID=9756412) and here [http://ubuntuforums.org/showthread.php?t=543965](http://ubuntuforums.org/showthread.php?t=543965)

6.  Visit [http://lejos.sourceforge.net](http://lejos.sourceforge.net) and download the lejos_NXT_0_6_0beta.tar.gz tarball (I saved it in /usr/bin/lejos)

7.  Unpack it:** tar xfvz  lejos_NXT_0_6_0beta.tar.gz**.

8.  Move it to the spot you want it: **sudo mv /usr/bin/lejos /user/share/lejos**.

9.  Give everyone read and write privileges:** chmod 777 /usr/share/lejos/bin --recursive**.

10.  Edit your .profile file by adding these lines to the very end so that you can build the leJOS installation, and then reboot: **sudo gedit ~.profile**

[b][list]export PATH=/usr/share/lejos/bin:$PATH
export PATH=/usr.share/ant/bin:$PATH
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.06
export NXT_HOME=/usr/share/lejos[/list][/b]

11.  Move to the /usr/share/lejos/build folder and run ant to build your installation: **ant**

12.  At this point it works with USB but not Bluetooth.  If you don't have root privileges, you can run run **sudo -s** to open a root window before using any of the nxt commands like nxjbrowse, nxjc or nxj.

13.  This is where you install the leJOS firmware.  Connect it to your computer using the USB cable and make sure it's on.  You will have to use a bent paperclip to depress the reset button in one of the grooves.  When the device starts audibly clicking. Run **nxjflash** from a root window.  There might be a data aborts&#8212;if it doesn't work, pop out a battery, put it back in and try again.

14.  Edit your .profile file to include the following and then reboot:
**sudo gedit ~/.profile**

[b][list]export PATH=/usr/share/lejos/lib:$PATH 
export PATH=/usr/share/lejos/3rdparty/lib:$PATH 
export CLASSPATH=/usr/share/lejos/lib/classes.jar:$CLASSPATH 
export CLASSPATH=/usr/share/lejos/lib/jtools.jar:$CLASSPATH 
export CLASSPATH=/usr/share/lejos/lib/pccomm.jar:$CLASSPATH 
export CLASSPATH=/usr/share/lejos/lib/pctools.jar:$CLASSPATH 
export CLASSPATH=/usr/share/lejos/3rdparty/lib/bcel-5.1.jar:$CLASSPATH 
export CLASSPATH=/usr/share/lejos/3rdparty/lib/bluecove.jar:$CLASSPATH 
export CLASSPATH=/usr/share/lejos/3rdparty/lib/bluecove203.jar:$CLASSPATH 
export CLASSPATH=/usr/share/lejos/3rdparty/lib/bluecove-gpl.jar:$CLASSPATH 
export CLASSPATH=/usr/share/lejos/3rdparty/lib/commons-cli-1.0.jar:$CLASSPATH 
export CLASSPATH=/usr/share/lejos/3rdparty/lib/cpptasks.jar:$CLASSPATH [/list][/b]

15.  Copy libjlibnxt.so from the /usr/share/lejos/bin folder to the /usr/lib/jvm/java-6-openjdk/jre/lib/i386 folder

16.  Add Bluetooth Analyzer to the Applications/Accessories menu

17.  Create a file called /etc/udev/rules/70-lego.rules with this content (you can find the idVendor for the dongle by running **lsusb**):

[b][list]BUS=="usb", SYSFS{idVendor}=="03eb", GROUP="lego", MODE="0660" /* Atmel */
BUS=="usb", SYSFS{idVendor}=="0694", GROUP="lego", MODE="0660" /* Lego */
BUS=="usb", SYSFS{idVendor}=="0a12", GROUP="lego", MODE="0660" /* Dongle */[/list][/b]

18.  Create a group called lego and add yourself to it in System/Administration/Users and Groups/Manage Groups

19.  Create file NXT.properties in /usr/share/lejos/bin, with **NXTCommBluetooth=lejos.pc.comm.NXTCommBluecove**  as the only text

20.  Plug in the dongle.  Ubuntu's Bluetooth Analyzer will open and an icon will appear in your panel

21.  Get the NXT's Bluetooth address with the **hcitool** scan command (it will look like this 00:16:53:05:CA:2C)

22.  You may need to delete the /var/lib/bluetooth/00:13:46:11:CD:01 directory (I found this in a forum posting and I tried doing this when I couldn't connect and it seemed to work):** rm -rf 00:13:46:11:CD:01**

23.  On the NXT brick turn on Bluetooth and enable visibility.  Search for your computer and add the device

24.  Run nxjbrowse from a terminal and, when prompted by Bluetooth Analyzer, provide the default NXT password **1234** (this is called pairing and should only have to be done once).  You should get a Java window popup prompting you to connect to your NXT brick.  Make a note of the name and MAC address

25.  You may need to go into Bluetooth Manager/Preferences and change the Mode of Operation to &#8220;Visible and Connectable for other devices&#8221;.  Also enable Receive Files from Remote Devices under File Transfer

26.  Reboot.  Make sure the NXT brick is on and Bluetooth is enabled and the device is visible.  Run nxjbrowse.  You should successfully connect.

27.  Move to the samples folder and compile BTReceive (nxjc BTReceive.java).  Compile BTSend (this one is compiled with javac as specified in the file comments).  Ensure that the NXT brick is on and Bluetooth is on and the device is visible.  Upload the BTReceive file to the NXT (nxj BTReceive).  If there is a data abort (which seems to occur from time to occasional time with this beta) you will have to remove a battery and restart the NXT and try to upload it again.

28.From your root window, run java BTSend [NXT_NAME] [NXT-Address].  You should see a stream of integers being exchanged between your computer and the brick.  Tada![list][/list][/list]

---

### Post by chaanakya_chiraag on 2008-08-07
Thanks a lot  :)  I had it working at one point then had to reinstall.  I completely forgot what I did before.  This helped a lot  :)  Thank you!!

---

### Post by chaanakya_chiraag on 2008-08-08
However there is an easier way to edit environment variables.  Go to a terminal and type```
cd /etc
``` and ```
 sudo gedit environment 
```.  However, beware of one thing.  Since the PATH variable is already defined, you should **append** the PATH modifications to the end of the line, just before the quotes.  And another thing, you don't need the```
export
``` command before every line when you edit the environment file.  Other than that, your method worked perfectly.  By the way, you don't need to create udev rules or even do all that classpath stuff.  Simply 'cd'ing to the directory with the java files and 'nxjc'ing it should do the trick.

---

### Post by chaanakya_chiraag on 2008-08-12
By the way, anybody having trouble using USB with the NXT should try ```
sudo -s
export NXJ_HOME=(path to lejos home directory)
export JAVA_HOME=(path to java home directory)
export PATH=$PATH:(path to lejos home directory)/bin:(path to java home directory)/bin
cd (path to lejos executables)
```
and execute whichever one you need.  However, this may not be the most convenient way.  In order to make the changes stick, you have to edit a file called bash.bashrc in /etc.  Then, add the previous environment variables and you should be good to go.

---

### Post by VancouverCowboy on 2008-08-26
Thanks that's great!

---

### Post by herrBua on 2008-09-06
How exactly do you edit the bash.bashrc file in /etc?

I mean, I have set up the PATH with the /bin from lejos, but I haven't been able to set up the NXJ_HOME variable.

By the way, I'm loving this thread... for real, loving it ^^

---

### Post by herrBua on 2008-09-06
I seem to be unable to compile the BTSend.java file. The compiler tells me that the error ocurrs when trying to import the "lejos.pc.comm" package.

There are a couple of parts of the whole list I didn't exactly do. For example, editing my .profile. Instead i edited the bash.bashrc adding the NXJ_HOME, JAVA_HOME and PATH lines.

> 14. Edit your .profile file to include the following and then reboot:
sudo gedit ~/.profile

    * export PATH=/usr/share/lejos/lib:$PATH
      export PATH=/usr/share/lejos/3rdparty/lib:$PATH
      export CLASSPATH=/usr/share/lejos/lib/classes.jar:$CLASSPATH
      export CLASSPATH=/usr/share/lejos/lib/jtools.jar:$CLASSPATH
      export CLASSPATH=/usr/share/lejos/lib/pccomm.jar:$CLASSPATH
      export CLASSPATH=/usr/share/lejos/lib/pctools.jar:$CLASSPATH
      export CLASSPATH=/usr/share/lejos/3rdparty/lib/bcel-5.1.jar:$CLASSPATH
      export CLASSPATH=/usr/share/lejos/3rdparty/lib/bluecove.jar:$CLASSPATH
      export CLASSPATH=/usr/share/lejos/3rdparty/lib/bluecove203.jar:$CLASSPATH
      export CLASSPATH=/usr/share/lejos/3rdparty/lib/bluecove-gpl.jar:$CLASSPATH
      export CLASSPATH=/usr/share/lejos/3rdparty/lib/commons-cli-1.0.jar:$CLASSPATH
      export CLASSPATH=/usr/share/lejos/3rdparty/lib/cpptasks.jar:$CLASSPATH


This part I also added to the bash.bashrc file, but I believe I did something wrong, because the CLASSPATH should have already been modified but the Java compiler tells me otherwise.

Inside of the BTSend.java file there's a line that says:
"On Linux, you will need libjbluez.so on the Java library path."

That's another thing I don't know how to do, edit the Java library path.

If you guys could help me out with this I'd really appreciate it. I'm almost done setting up lejos in Ubuntu and I'd really like to finish this.

By the way, my bash.bashrc looks like this:

> # System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

# Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
# If this is an xterm set the title to user@host:dir
#case "$TERM" in
#xterm*|rxvt*)
#    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
#    ;;
#*)
#    ;;
#esac

# enable bash completion in interactive shells
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

# sudo hint
if [ ! -e $HOME/.sudo_as_admin_successful ]; then
    case " $(groups) " in *\ admin\ *)
    if [ -x /usr/bin/sudo ]; then
	cat <<-EOF
	To run a command as administrator (user "root"), use "sudo <command>".
	See "man sudo_root" for details.
	
	EOF
    fi
    esac
fi

# if the command-not-found package is installed, use it
if [ -x /usr/lib/command-not-found ]; then
	function command_not_found_handle {
	        # check because c-n-f could've been removed in the meantime
                if [ -x /usr/lib/command-not-found ]; then
		   /usr/bin/python /usr/lib/command-not-found -- $1
                   return $?
		else
		   return 127
		fi
	}
fi

NXJ_HOME=/home/kurt/lejos_nxj
JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.06
PATH=$PATH:/home/kurt/lejos_nxj/bin:/usr/lib/jvm/java-6-sun-1.6.0.06/bin

PATH=$PATH:/home/kurt/lejos_nxj/lib
PATH=$PATH:/home/kurt/lejos_nxj/lib
CLASSPATH=$CLASSPATH:/home/kurt/lejos_nxj/lib/classes.jar
CLASSPATH=$CLASSPATH:/home/kurt/lejos_nxj/lib/jtools.jar
CLASSPATH=$CLASSPATH:/home/kurt/lejos_nxj/lib/pccomm.jar
CLASSPATH=$CLASSPATH:/home/kurt/lejos_nxj/lib/pctools.jar
CLASSPATH=$CLASSPATH:/home/kurt/lejos_nxj/3rdparty/lib/bcel-5.1.jar
CLASSPATH=$CLASSPATH:/home/kurt/lejos_nxj/3rdparty/lib/bluecove.jar
CLASSPATH=$CLASSPATH:/home/kurt/lejos_nxj/3rdparty/lib/bluecove203.jar
CLASSPATH=$CLASSPATH:/home/kurt/lejos_nxj/3rdparty/lib/bluecove-gpl.jar
CLASSPATH=$CLASSPATH:/home/kurt/lejos_nxj/3rdparty/lib/commons-cli-1.0.jar
CLASSPATH=$CLASSPATH:/home/kurt/lejos_nxj/3rdparty/lib/cpptasks.jar

I'm sorry that my post is this big, but I wanted to write as detailed as possible.

Thank you in advance.

---

### Post by VancouverCowboy on 2008-09-09
All I can suggest is you start over at the top of the list and do everything in it.  If you skip some steps, then I can't guarantee it'll work.  Make sure you've done every single step and then tell us what your systems does...

---

### Post by chaanakya_chiraag on 2008-10-26
To load the libjbluez.so module, copy the libjbluez.so(.bak?) to /lib and set correct permissions.  Then in BTSend, add the following line right before the lejos.pccomm line:
```
Runtime.getRuntime().load("/lib/libjbluez.so");
```
That should fix that problem.  I had to do a **LOT** of research before I stumbled upon this one.
Wait, there's an asterisk next to the first export.  Try removing that and see if that fixes things.  If it doesn't, try running the following code in Terminal:
```
echo $CLASSPATH
```
If this returns an empty line, your classpath is not being set at all. If it displays what you have posted, then I have no clue why the Java compiler is not recognizing the classpath and I can't help you further.

By the way, here's my bash.bashrc:

```
# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

# Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
# If this is an xterm set the title to user@host:dir
#case "$TERM" in
#xterm*|rxvt*)
#    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
#    ;;
#*)
#    ;;
#esac

# enable bash completion in interactive shells
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

# sudo hint
if [ ! -e $HOME/.sudo_as_admin_successful ]; then
    case " $(groups) " in *\ admin\ *)
    if [ -x /usr/bin/sudo ]; then
	cat <<-EOF
	To run a command as administrator (user "root"), use "sudo <command>".
	See "man sudo_root" for details.
	
	EOF
    fi
    esac
fi

# if the command-not-found package is installed, use it
if [ -x /usr/lib/command-not-found ]; then
	function command_not_found_handle {
	        # check because c-n-f could've been removed in the meantime
                if [ -x /usr/lib/command-not-found ]; then
		   /usr/bin/python /usr/lib/command-not-found -- $1
                   return $?
		else
		   return 127
		fi
	}
fi

export NXJ_HOME=/usr/share/lejos_nxj
export JAVA_HOME=/home/chiraag/jdk1.6.0_10
export PATH=$PATH:/usr/share/lejos_nxj/bin:/home/chiraag/jdk1.6.0_10/bin
export PATH=/usr/share/lejos_nxj/lib:$PATH
export PATH=/usr/share/lejos_nxj/3rdparty/lib:$PATH
export CLASSPATH=.:$CLASSPATH
export CLASSPATH=/usr/share/lejos_nxj/lib/classes.jar:$CLASSPATH
export CLASSPATH=/usr/share/lejos_nxj/lib/jtools.jar:$CLASSPATH
export CLASSPATH=/usr/share/lejos_nxj/lib/pccomm.jar:$CLASSPATH
export CLASSPATH=/usr/share/lejos_nxj/lib/pctools.jar:$CLASSPATH
export CLASSPATH=/usr/share/lejos_nxj/3rdparty/lib/bcel-5.1.jar:$CLASSPATH
export CLASSPATH=/usr/share/lejos_nxj/3rdparty/lib/bluecove.jar:$CLASSPATH
export CLASSPATH=/usr/share/lejos_nxj/3rdparty/lib/bluecove203.jar:$CLASSPATH
export CLASSPATH=/usr/share/lejos_nxj/3rdparty/lib/bluecove-gpl.jar:$CLASSPATH
export CLASSPATH=/usr/share/lejos_nxj/3rdparty/lib/commons-cli-1.0.jar:$CLASSPATH
export CLASSPATH=/usr/share/lejos_nxj/3rdparty/lib/cpptasks.jar:$CLASSPATH

```

---

### Post by chaanakya_chiraag on 2008-10-31
Darn it!  I just upgraded to intrepid and when i try to connect to the nxt, it says connecting and hangs there.  Anybody know what to do?

---

### Post by chaanakya_chiraag on 2008-10-31
Dev team!  Please fix the bluetooth problem QUICKLY (as in within the next three days!)  I have a research project that DEPENDS on bluetooth in order to work properly!  This is a BIG hassle because I cannot test my program while this problem persists.  PLEASE FIX THE BLUETOOTH QUICKLY!!!
Thanks:)

---

### Post by VancouverCowboy on 2008-12-13
Have you solved your Bluetooth problem yet?

---

### Post by chaanakya_chiraag on 2008-12-13
Kind of.  I need a dongle with [at least] 4 ports to work.  I have only gotten a 1-port dongle to work :(  I got the 1-port dongle working by installing blueman's repo and basically updating to the bleeding edge version of bluez.  I still can't believe the devs still haven't fixed it!  I mean, lots, and I mean LOTS, need bluetooth.  It's not like only a few people need it.  For some people (like me), bluetooth is the only way to communicate with their phone, which means that I can't run my NXT project and transfer stuff to my phone at the same time.  To be honest, I'm surprised that even one dongle is working.  Still, the devs need to be a little more responsive.  Devs, why did you do this?

---

### Post by kamazu on 2009-01-19
We're trying to run LejOS-0.7 on 8.04 and when we try running nxj we get the error:
```

$  nxj -r Tune
leJOS NXJ> Linking...
leJOS NXJ> Uploading...
leJOS NXJ> Cannot load USB driver
```We tried nxjbrowse --usb as well:
```

$ nxjbrowse --usb
Error: Cannot load a comm driver

```We have both libusb and libusb-dev installed:
```

$ aptitude search libusb
i   libusb-0.1-4                    - userspace USB programming library         
i   libusb-dev                      - userspace USB programming library developm

```We've tried running as root and non-root with no effect. We've tried chmod'ing the correct devices under /dev/bus/usb/* with no effect.

We are lost :-(

Any ideas what the problem might be or how we could test it?

---

### Post by chaanakya_chiraag on 2009-01-22
@kamazu:  I have no clue what the heck is going on.  All I can suggest is that you try removing libusb and libusb-dev and reinstall.  If that doesn't work, I don't know what to do.

By the way, **DO NOT UPGRADE TO INTREPID!!!!!!!!!**  I upgraded and couldn't get the bluetooth working.  So for now, I've downgraded (upgraded?) to Hardy.

[Update] You can now install jaunty.  Bluetooth now works in Jaunty.

---

### Post by Ludachrispeed on 2010-02-27
Hello everybody! I had a lot of trouble getting BTSend to run, but I just did, and I wanted let ya'll know what happened.

I just copied all those CLASSPATH lines in my .profile to my root user's .profile, then compile and run as root.

HOW TO DO THAT:

Open a terminal and type the following command to look at your .profile:

```
gedit ~/.profile
```

Open a new terminal and switch to root user:

```
sudo su
```

Then open the root user's .profile:

```
gedit .profile
```

Then just copy all those lines from the first .profile that you opened to the second .profile that you opened.

In the second terminal, type

```
exit
```

to leave root.

Now cd to the directory with BTSend in it, switch to root (using sudo su), compile (with javac) and run (java BTSend [NXT-name])

EDIT: I just found that this only works if I first cd to the directory with BTSend, then type "sudo su", then type ". ~/.profile" in the terminal right before trying to compile and run.  That second command forces the terminal to reread it's .profile.  I have no idea why I have to keep giving that command every time, right before compilation and running.

---

