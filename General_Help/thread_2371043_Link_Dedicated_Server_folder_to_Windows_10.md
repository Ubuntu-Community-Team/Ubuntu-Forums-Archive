---
title: "Link Dedicated Server folder to Windows 10"
date: 2017-09-10
forum: General Help
---

### Post by forcefire on 2017-09-10
Hi all

I have a dedicated server running Ubuntu Server 14.04 "Trusty Tahr" LTS which is 3X4TB drives unraided into a single 12TB storage drive, its got no "desktop" environment either so I can't use XFCE like I do with my seedbox so I access it to do everything via Putty on my Windows 10 machine. What I want is to create a folder on the server that I can map on my Windows PC so I can access all files without having to either use Putty or an FTP program. 

I'm still new to Linux but have been learning my way round but doing this is something I'd rather ask for help on than just google and make a mistake. If anyone can offer some advice that would be great. 

Thank you

---

### Post by Erik1984 on 2017-09-10
Samba sounds like what you are looking for: [https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)

---

### Post by forcefire on 2017-09-10
Hi

Would this guide be better: [https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way)! as I don't have any desktop access to the Ubuntu server so it all has to be command line

---

### Post by SeijiSensei on 2017-09-10
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by forcefire on 2017-09-12
[SIZE=5]Hi

OK, I'm having issues as I'm sure I've either missed something or done something wrong. Every time I try and map the folder on my Ubuntu Server to my Windows 10 PC it fails. 

First I did this:[/SIZE]

[LIST]
[*=left]Install Samba
[LIST]
[*=left]
[B]sudo apt-get update
sudo apt-get install samba[/B]
[/LIST]

[*=left]Set a password for your user in Samba
[LIST]
[*=left]
**sudo smbpasswd -a <user_name>**
[LIST]
[*=left]Note: Samba uses a separate set of passwords than the standard Linux system accounts (stored in /etc/samba/smbpasswd), so you'll need to create a Samba password for yourself. This tutorial implies that you will use your own user and it does not cover situations involving other users passwords, groups, etc...Tip1: Use the password for your own user to facilitate.Tip2: Remember that your user must have permission to write and edit the folder you want to share.
Eg.:
sudo chown <user_name> /var/opt/blah/blahblah
sudo chown :<user_name> /var/opt/blah/blahblahTip3: If you're using another user than your own, it needs to exist in your system beforehand, you can create it without a shell access using the following command :
sudo useradd USERNAME --shell /bin/false

You can also hide the user on the login screen by adjusting lightdm's configuration, in /etc/lightdm/users.conf add the newly created user to the line :
hidden-users=
[/LIST]
[/LIST]

[*=left]Create a directory to be shared
**mkdir /home/<user_name>/<folder_name>**
[*=left]Make a safe backup copy of the original smb.conf file to your home folder, in case you make an error
**sudo cp /etc/samba/smb.conf ~**
[*=left]Edit the file "/etc/samba/smb.conf"
**sudo nano /etc/samba/smb.conf**
[LIST]
[*=left]Once "smb.conf" has loaded, add this to the very end of the file:

[<folder_name>]
path = /home/<user_name>/<folder_name>
valid users = <user_name>
read only = noTip: There Should be in the spaces between the lines, and note que also there should be a single space both before and after each of the equal signs.
[/LIST]

[*=left]Restart the samba:
[B]sudo service smbd restart
[/B]
[*=left]
[/LIST]
[LEFT][SIZE=5]Then I tried this:
[/SIZE]
**Samba Server Configuration in terminal**

[COLOR=#333333][FONT=Ubuntu]Configuration is performed by reading and editing **/etc/samba/smb.conf**, the configuration file for the samba server.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]The following tips show how to do some basic things without installing additional software, using the command line. It is not difficult, just be careful with typos.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]First open a terminal: **Applications** > **System Tools** > **Terminal** and open the file smb.conf[/FONT][/COLOR]

sudo nano -w /etc/samba/smb.conf[COLOR=#333333][FONT=Ubuntu]**How to Save:** To save in nano use "CTRL-O", then "CTRL-X".[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]**Tip:** Replacing **sudo nano** with **gksudo gedit** gives you a nice graphical editor.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]The file *smb.conf* is divided in several sections:[/FONT][/COLOR]

Global Settings
Debugging/Accounting
Authentication
Printing
File sharing
Misc
Share Definitions[COLOR=#333333][FONT=Ubuntu]**Comments may start with either a # or a ;**[/FONT][/COLOR]
**Global Settings**

[COLOR=#333333][FONT=Ubuntu]Let's start with **Global Settings**. Here you will see several lines, which you can also see in the graphical networktool like workgroup and wins server. If you changed everything to your liking already then you can skip this section, if not change to what you need. If you do not know what items mean, leave them be and read the [relevant part in the real Samba-howto]("http://www.samba.org/samba/docs/using_samba/ch06.html") instead of randomly changing them. It will save you trouble-shooting later.[/FONT][/COLOR]
**File Sharing (Basics)**

[COLOR=#333333][FONT=Ubuntu]The important part for us is **File sharing**. Samba shares are named in brackets, [ ], and configured by adding options in the lines that follow. Most options are boolean (yes / no).[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]We need to change:[/FONT][/COLOR]

[homes]
comment = Home Directories
browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
  writable = no[COLOR=#333333][FONT=Ubuntu]This describes your /home directory. Usually you want to share this directory in a home environment, because these are the files you want to share. To do so, make the following changes:[/FONT][/COLOR]

[homes]
comment = Home Directories
browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no[COLOR=#333333][FONT=Ubuntu]This finishes sharing your /home directory. The last thing we need to do is fixing a user.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Add users who can access your shares with the 'smbpasswd' command.[/FONT][/COLOR]

sudo  smbpasswd -a username

New SMB password:
Retype new SMB password:
Added user username.

sudo smbpasswd -e username
Enabled user username.[COLOR=#333333][FONT=Ubuntu]NOTE: the username used here should be a real user setup on your PC/Server. Reload Samba for every change to users/passwords or 'smb.conf'[/FONT][/COLOR]

sudo /etc/init.d/samba reload[COLOR=#333333][FONT=Ubuntu][FONT=inherit]NOTE[/FONT]: If the above command doesn't work for you, try:[/FONT][/COLOR]
sudo smbd reload

[SIZE=5][COLOR=#333333][FONT=Ubuntu]
But neither worked so I'm stumped, I only want to be able to access 1 folder on my Ubuntu Server (/home/VOD) on my windows PC so I can rename the files if I need to and move them about in to new sub-folders (home/VOD/Files1 or home/VOD/Files2). If it helps the server is provided by OVH and has no desktop GUI. Its Ubuntu Server 14.04 "Trusty Tahr" 64bit version

Please can someone just offer a simple way to achieve what I need, I'm just confused now with all the guides offered, lol[/FONT][/COLOR][/SIZE]

[/LEFT]

---

