---
title: "HOWTO: Taking seamlessrdp and making it more &quot;seamless&quot;"
date: 2007-03-22
forum: General Help
---

### Post by statictonic on 2007-03-22
Note this is the first guide I have written before so it might not be the best, any suggestions and fixes are welcome!

**The files necessary in this guide are attached to this post.**

[COLOR="Red"][SIZE="5"]**HOWTO do more with SeamlessRDP**[/SIZE][/COLOR]

This guide will help you to run multiple windows applications easily from the console, as well as installing items into windows from the console.  It will also allow you to open things such as jpg's in windows easily while still using linux.

Please note, that this is using an unsecured password free telnet connection to launch applications on Windows XP, because of this anyone can start applications on the Windows XP computer, which makes for a bit of a security hole, however if your on a private network behind a firewall of any sort this shouldn't be a big deal.  Also take note that this is far from perfect, and definitely not problem free.  This guide and the scripts come with no warranty.

This guide will not cover the install of Windows XP onto a virtual machine nor will it cover the initial rdesktop, and seamlessrdp setup.  For information on setting up a virtual machine I will refer you to [this guide]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo").  After that guide follow [this guide]("https://help.ubuntu.com/community/SeamlessVirtualization") for the initial setup and install, this will get you to a point in which you can have a single window up an running from a command using rdesktop.

This guide will help you take this a step further yet.  To allow for the ability to run multiple applications with short and simple commands, and to be able to install applications sitting on your linux partition with ease.  

On your windows xp install, you may have to make changes to firewall settings in order for this to work properly.

[COLOR="Red"][SIZE="3"]**PART 1 Running multiple applications from shortcuts or from the console.**[/SIZE][/COLOR]

First what you need to do on your windows virtual machine is download the php installer.  [This is a link to a mirror listing for the XP installer, choose one and download it on your virtual machine.]("http://www.php.net/get/php-5.2.1-win32-installer.msi/from/a/mirror")  

Once the download has completed you need to install it, you can stick with the defaults on everything except there is one additional item you need to select to install.  You will need to open up the extensions section and select to install Sockets.  You can then continue through the rest of the install.

Now that PHP is installed you need to add a few files to the XP install that will be necessary.

Extract the batch.zip(included the tar archive with the other files and this howto) file to "c:\start\", it does need to be in exactly that file to work.  Once you are done with you should log out of Windows XP.  

The scripts that connect to the XP machine require an additional application called expect.  It does not come with Ubuntu by default.  To get it run "sudo apt-get install expect"

With the files included in the tar, there is one called, windows, open it with a text editor such as gedit.  There are two places where you need to enter the IP address of the window install using VMWare, do so and save it.

Run the install included with the tar archive script(note you must be root or use sudo)"sudo ./install"  You may need to add execute permission to it first, use chmod +x install.

After you have done that, it's time to connect using the rdesktop command:
"rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\start\batch.exe" 0.0.0.0 -u INSERTUSER -p INSERTPASSWORD"
Note c:\start\batch.exe leave it as that.  After running this command a window will pop up for a few seconds logging into windows then it should disappear, nothing will be displayed.

Now open up a command console, type "windows iexplore" it should launch Internet Explorer.  You can also create shortcuts using this command.  You should be able to run as many applications as you would like using this command.

NOTE: This does not currently work correctly with slashes as far as I know, so if you want to run an application the best solution is to stick a shortcut in the "c:\Documents and Settings\Youruser" directory.  This will allow you to be able to simple type "windows nameofshortcut".



[SIZE="3"][COLOR="Red"]**PART 2, sharing files between Linux and Windows, and installing/launching files from your Ubuntu partition onto your virtual machines in a new windows.**[/COLOR][/SIZE]

Run the following commands:
sudo mkdir /mnt/windowsrdp
#NOTE: change to your username below.
sudo chown yourprimarylinuxuser /mnt/windowsrdp

Next you will need to install samba.  "sudo apt-get install samba"

Once samba is installed, you will need to create a samba user.  To do this type smbpasswd -a yourusername
It will prompt you for a password, enter in whatever you would like it to be, this does not have to be the same one you use for your system under that username.

Now we need to add a share for that folder, to do this run "sudo gedit /etc/samba/smb.conf"
Scroll down to the very bottom of the file and add the following lines.

#Start
[Linux]
path = /mnt/windowsrdp
available = yes
browseable = yes
public = yes
writable = yes
guest ok = no
#End

After that is done, you should then restart samba, although this is generally not required.  "sudo /etc/init.d/samba restart"

Now open up your virtual machine window, open up My Computer or another folder, and in the address bar type \\youripaddress obviously replacing what I put with your IP address.  You should see a folder called linux, right click on it, and click map to network drive.  You want to give it drive letter Z, note that it has to be Z unless you change it yourself in the script that was installed previously.  Enter in the username and password you setup with samba when you ran "smbpasswd -a".  Make sure to check "Reconnect and logon".

Now you should be able to log off of Windows.

It's time to connect using the rdesktop command:
"rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\start\batch.exe" 0.0.0.0 -u INSERTUSER -p INSERTPASSWRD"

Note c:\start\batch.exe leave it as that.  After running this command a window will pop up for a few seconds logging into windows then it should disappear, nothing will be displayed.  Also make sure to change 0.0.0.0 to be the IP address of your virtual machine.

Now find an exe or a jpg for that matter from the terminal, and type "windows -install someprogram.exe" replaceing someprogram.exe with the actual program or with an image for that matter.  It will then open it up on the Windows machine in an individual window on your Linux Desktop.

NOTE when this command is run it is making a copy of that file, to the /mnt/windowsrdp directory.  The files will stay there until you delete them.  Also as of current, if there are any files that go with the exe, they will not be transfered therefore it will not work correctly.

---

### Post by edmondt on 2007-03-22
Interesting how to :) It just keeps getting better and better :D

---

### Post by Eddie Hung on 2007-04-15
Could the creator please explain how this works?

Eddie

---

### Post by statictonic on 2007-04-21
> **Eddie Hung said:**
> Could the creator please explain how this works?

Eddie

Essentially you're starting up a single exe with seamlessrdp.  The program doesn't have any windows popup, it does run a php script though that allows to launching of programs via a telnet connection.  The shell script allows you to make a nice simple command to launch a program via telnet.

Otherwise you could telnet to that ip address and type start iexplore for example.

---

### Post by _haz on 2007-05-04
> **statictonic said:**
> Essentially you're starting up a single exe with seamlessrdp.  The program doesn't have any windows popup, it does run a php script though that allows to launching of programs via a telnet connection.  The shell script allows you to make a nice simple command to launch a program via telnet.

Otherwise you could telnet to that ip address and type start iexplore for example.

If you're feeling a bit adventurous and are confident compiling from source, you could try a patch for rdesktop that we've been putting together to add support for multiple applications and some other features. The files and brief instructions are available from [https://www.fontis.com.au/rdesktop]("https://www.fontis.com.au/rdesktop") .

---

### Post by BlackHatRob on 2008-02-08
I have yet to have been able to use seamlessrdp with ubuntu 7.10. Currently, when I run the rdesktop command  "rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\start\batch.exe" x.x.x.x -u <username> -d <domain> -p -" I create an RDP session but it doesn't disappear. Instead, the rdp session is full screen on my desktop. Any ideas?

---

### Post by sp00ki on 2008-02-12
From what i've noticed, the problem is with your domain's "welcome message" (aka interactive logon message) which is often configured on corporate domains.  This pretty much stands in the way of any automated login attempts-- this one included.
I'm going to try disabling the message from GPO and seeing if it works; i'll post an update with any info.

**
ed:  scratch that, disabled it and having the same issue.  i'm looking for a possible solution, lemme know if you find one!

---

### Post by kevcool on 2008-03-13
I have the same problem.  I'm logged into the full desktop rather than the applications I specify.  This is Ubuntu 7.10.  Thanks if anyone's aware of a solution.

---

