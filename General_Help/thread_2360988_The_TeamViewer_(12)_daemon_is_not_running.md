---
title: "The TeamViewer (12) daemon is not running"
date: 2017-05-10
forum: General Help
---

### Post by Robbyx on 2017-05-10
*TV does not offer support to non licensed users. What can I  do next?*

I have installed it according to the advice at [https://ubuntuforums.org/archive/index.php/t-2329353.html?login=1]("https://ubuntuforums.org/archive/index.php/t-2329353.html?login=1"). In particular I have following this part but changing the version to TV 12

> I downloaded the v11.0.57095 (deb 32-Bit / 64-Bit Multiarch) from the official website ([https://www.teamviewer.com/en/download/linux/](https://www.teamviewer.com/en/download/linux/)) and then typed on the terminal 
sudo dpkg -i teamviewer_11.0.57095_i386.deb

Good Job!:) That is what I hoped you did
TeamViewer has a script called teamviewerd.sysv available in /opt/teamviewer/tv_bin/script. 

All you need to do is make sure this script runs on startup. Making sure of this is relatively simple, just copy it to /etc/init.d like so:


cd /opt/teamviewer/tv_bin/script
sudo cp teamviewerd.sysv /etc/init.d/

Don't forget to make the script non-writable to anyone but the owner!


sudo chmod 755 /etc/init.d/teamviewerd.sysv

Then run


sudo update-rc.d teamviewerd.sysv defaults

The service will now start automatically with each boot. If you don't feel like rebooting, you can start the service manually with:


sudo service teamviewerd.sysv start

When having followed the installation advice and clicked on the TV icon to start it up I get an error report from TV: > The TV daemon is not running. Please start the daemon (needs root permissions) before running TV.

I get the same error message from running the instuctions at 

[https://askubuntu.com/questions/912872/cant-install-teamviewer-12-on-ubuntu-16-04-64bit-dependency-lib32asound2]("https://askubuntu.com/questions/912872/cant-install-teamviewer-12-on-ubuntu-16-04-64bit-dependency-lib32asound2")

I have even tried to install TV 10, but get the same error message as for 12.


Robin

---

### Post by howefield on 2017-05-10
Thread moved to the "*General Help*" forum.

---

### Post by howefield on 2017-05-10
I've tried installing Teamviewer 12.76279 with apt and it works fine in vanilla Ubuntu  

```
sudo apt install ~/Downloads/Packages/teamviewer_12.0.76279_i386.deb 
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'teamviewer:i386' instead of '/home/hugh/Downloads/Packages/teamviewer_12.0.76279_i386.deb'
The following additional packages will be installed:
  gcc-6-base:i386 libasound2:i386 libc6:i386 libdbus-1-3:i386 libexpat1:i386 libfontconfig1:i386 libfreetype6:i386 libgcc1:i386
  libgcrypt20:i386 libgpg-error0:i386 libice6:i386 libjpeg62:i386 liblz4-1:i386 liblzma5:i386 libpcre3:i386 libpng16-16:i386
  libselinux1:i386 libsm6:i386 libsystemd0:i386 libuuid1:i386 libx11-6:i386 libxau6:i386 libxcb1:i386 libxdamage1:i386 libxdmcp6:i386
  libxext6:i386 libxfixes3:i386 libxinerama1:i386 libxrandr2:i386 libxrender1:i386 libxtst6:i386 zlib1g:i386
Suggested packages:
  libasound2-plugins:i386 glibc-doc:i386 locales:i386 rng-tools:i386
The following NEW packages will be installed
  gcc-6-base:i386 libasound2:i386 libc6:i386 libdbus-1-3:i386 libexpat1:i386 libfontconfig1:i386 libfreetype6:i386 libgcc1:i386
  libgcrypt20:i386 libgpg-error0:i386 libice6:i386 libjpeg62:i386 liblz4-1:i386 liblzma5:i386 libpcre3:i386 libpng16-16:i386
  libselinux1:i386 libsm6:i386 libsystemd0:i386 libuuid1:i386 libx11-6:i386 libxau6:i386 libxcb1:i386 libxdamage1:i386 libxdmcp6:i386
  libxext6:i386 libxfixes3:i386 libxinerama1:i386 libxrandr2:i386 libxrender1:i386 libxtst6:i386 teamviewer:i386 zlib1g:i386
0 to upgrade, 33 to newly install, 0 to remove and 0 not to upgrade.
Need to get 5,677 kB/52.2 MB of archives.
After this operation, 170 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 gcc-6-base i386 6.3.0-12ubuntu2 [17.4 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libgcc1 i386 1:6.3.0-12ubuntu2 [48.0 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libc6 i386 2.24-9ubuntu2 [2,278 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libpcre3 i386 2:8.39-3 [227 kB]
Get:5 /Data/Downloads/Packages/teamviewer_12.0.76279_i386.deb teamviewer i386 12.0.76279 [46.5 MB]
Get:6 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libgpg-error0 i386 1.26-2 [37.4 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libgcrypt20 i386 1.7.6-1 [372 kB]
Get:8 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 liblz4-1 i386 0.0~r131-2ubuntu2 [38.0 kB]
Get:9 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 liblzma5 i386 5.2.2-1.2 [98.7 kB]
Get:10 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libselinux1 i386 2.6-3 [73.3 kB]
Get:11 http://gb.archive.ubuntu.com/ubuntu zesty-updates/main i386 libsystemd0 i386 232-21ubuntu3 [228 kB]
Get:12 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libxau6 i386 1:1.0.8-1 [8,352 B]
Get:13 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libxdmcp6 i386 1:1.1.2-1.1 [11.4 kB]
Get:14 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libxcb1 i386 1.11.1-1ubuntu1 [44.1 kB]
Get:15 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libx11-6 i386 2:1.6.4-3 [594 kB]
Get:16 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libxext6 i386 2:1.3.3-1 [31.6 kB]
Get:17 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libice6 i386 2:1.0.9-1 [38.2 kB]
Get:18 http://gb.archive.ubuntu.com/ubuntu zesty/universe i386 libjpeg62 i386 1:6b2-2 [80.5 kB]
Get:19 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libuuid1 i386 2.29-1ubuntu2 [15.7 kB]
Get:20 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libsm6 i386 2:1.2.2-1 [14.8 kB]
Get:21 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libxdamage1 i386 1:1.1.4-2 [6,812 B]
Get:22 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libxinerama1 i386 2:1.1.3-1 [7,900 B]
Get:23 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 zlib1g i386 1:1.2.11.dfsg-0ubuntu1 [55.5 kB]
Get:24 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libdbus-1-3 i386 1.10.10-1ubuntu2 [175 kB]
Get:25 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libexpat1 i386 2.2.0-2 [75.0 kB]
Get:26 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libpng16-16 i386 1.6.28-1 [181 kB]
Get:27 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libasound2 i386 1.1.3-5 [380 kB]
Get:28 http://gb.archive.ubuntu.com/ubuntu zesty-updates/main i386 libfreetype6 i386 2.6.3-3ubuntu2.2 [336 kB]
Get:29 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libfontconfig1 i386 2.11.94-0ubuntu2 [140 kB]
Get:30 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libxfixes3 i386 1:5.0.3-1 [11.2 kB]
Get:31 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libxrender1 i386 1:0.9.10-1 [19.9 kB]
Get:32 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libxrandr2 i386 2:1.5.1-1 [19.9 kB]
Get:33 http://gb.archive.ubuntu.com/ubuntu zesty/main i386 libxtst6 i386 2:1.2.3-1 [13.4 kB]
Fetched 5,677 kB in 1s (2,992 kB/s)       
Extract templates from packages: 100%
Preconfiguring packages ...
Selecting previously unselected package gcc-6-base:i386.
(Reading database ... 211387 files and directories currently installed.)
Preparing to unpack .../0-gcc-6-base_6.3.0-12ubuntu2_i386.deb ...
Unpacking gcc-6-base:i386 (6.3.0-12ubuntu2) ...
Selecting previously unselected package libgcc1:i386.
Preparing to unpack .../1-libgcc1_1%3a6.3.0-12ubuntu2_i386.deb ...
Unpacking libgcc1:i386 (1:6.3.0-12ubuntu2) ...
Selecting previously unselected package libc6:i386.
Preparing to unpack .../2-libc6_2.24-9ubuntu2_i386.deb ...
Unpacking libc6:i386 (2.24-9ubuntu2) ...
Selecting previously unselected package libpcre3:i386.
Preparing to unpack .../3-libpcre3_2%3a8.39-3_i386.deb ...
Unpacking libpcre3:i386 (2:8.39-3) ...
Selecting previously unselected package libgpg-error0:i386.
Preparing to unpack .../4-libgpg-error0_1.26-2_i386.deb ...
Unpacking libgpg-error0:i386 (1.26-2) ...
Selecting previously unselected package libgcrypt20:i386.
Preparing to unpack .../5-libgcrypt20_1.7.6-1_i386.deb ...
Unpacking libgcrypt20:i386 (1.7.6-1) ...
Selecting previously unselected package liblz4-1:i386.
Preparing to unpack .../6-liblz4-1_0.0~r131-2ubuntu2_i386.deb ...
Unpacking liblz4-1:i386 (0.0~r131-2ubuntu2) ...
Selecting previously unselected package liblzma5:i386.
Preparing to unpack .../7-liblzma5_5.2.2-1.2_i386.deb ...
Unpacking liblzma5:i386 (5.2.2-1.2) ...
Selecting previously unselected package libselinux1:i386.
Preparing to unpack .../8-libselinux1_2.6-3_i386.deb ...
Unpacking libselinux1:i386 (2.6-3) ...
Setting up gcc-6-base:i386 (6.3.0-12ubuntu2) ...
Setting up libgcc1:i386 (1:6.3.0-12ubuntu2) ...
Setting up libc6:i386 (2.24-9ubuntu2) ...
Setting up libgpg-error0:i386 (1.26-2) ...
Setting up libgcrypt20:i386 (1.7.6-1) ...
Setting up liblz4-1:i386 (0.0~r131-2ubuntu2) ...
Setting up liblzma5:i386 (5.2.2-1.2) ...
Setting up libpcre3:i386 (2:8.39-3) ...
Setting up libselinux1:i386 (2.6-3) ...
Selecting previously unselected package libsystemd0:i386.
(Reading database ... 211709 files and directories currently installed.)
Preparing to unpack .../00-libsystemd0_232-21ubuntu3_i386.deb ...
Unpacking libsystemd0:i386 (232-21ubuntu3) ...
Selecting previously unselected package libxau6:i386.
Preparing to unpack .../01-libxau6_1%3a1.0.8-1_i386.deb ...
Unpacking libxau6:i386 (1:1.0.8-1) ...
Selecting previously unselected package libxdmcp6:i386.
Preparing to unpack .../02-libxdmcp6_1%3a1.1.2-1.1_i386.deb ...
Unpacking libxdmcp6:i386 (1:1.1.2-1.1) ...
Selecting previously unselected package libxcb1:i386.
Preparing to unpack .../03-libxcb1_1.11.1-1ubuntu1_i386.deb ...
Unpacking libxcb1:i386 (1.11.1-1ubuntu1) ...
Selecting previously unselected package libx11-6:i386.
Preparing to unpack .../04-libx11-6_2%3a1.6.4-3_i386.deb ...
Unpacking libx11-6:i386 (2:1.6.4-3) ...
Selecting previously unselected package libxext6:i386.
Preparing to unpack .../05-libxext6_2%3a1.3.3-1_i386.deb ...
Unpacking libxext6:i386 (2:1.3.3-1) ...
Selecting previously unselected package libice6:i386.
Preparing to unpack .../06-libice6_2%3a1.0.9-1_i386.deb ...
Unpacking libice6:i386 (2:1.0.9-1) ...
Selecting previously unselected package libjpeg62:i386.
Preparing to unpack .../07-libjpeg62_1%3a6b2-2_i386.deb ...
Unpacking libjpeg62:i386 (1:6b2-2) ...
Selecting previously unselected package libuuid1:i386.
Preparing to unpack .../08-libuuid1_2.29-1ubuntu2_i386.deb ...
Unpacking libuuid1:i386 (2.29-1ubuntu2) ...
Selecting previously unselected package libsm6:i386.
Preparing to unpack .../09-libsm6_2%3a1.2.2-1_i386.deb ...
Unpacking libsm6:i386 (2:1.2.2-1) ...
Selecting previously unselected package libxdamage1:i386.
Preparing to unpack .../10-libxdamage1_1%3a1.1.4-2_i386.deb ...
Unpacking libxdamage1:i386 (1:1.1.4-2) ...
Selecting previously unselected package libxinerama1:i386.
Preparing to unpack .../11-libxinerama1_2%3a1.1.3-1_i386.deb ...
Unpacking libxinerama1:i386 (2:1.1.3-1) ...
Selecting previously unselected package zlib1g:i386.
Preparing to unpack .../12-zlib1g_1%3a1.2.11.dfsg-0ubuntu1_i386.deb ...
Unpacking zlib1g:i386 (1:1.2.11.dfsg-0ubuntu1) ...
Selecting previously unselected package libdbus-1-3:i386.
Preparing to unpack .../13-libdbus-1-3_1.10.10-1ubuntu2_i386.deb ...
Unpacking libdbus-1-3:i386 (1.10.10-1ubuntu2) ...
Selecting previously unselected package libexpat1:i386.
Preparing to unpack .../14-libexpat1_2.2.0-2_i386.deb ...
Unpacking libexpat1:i386 (2.2.0-2) ...
Selecting previously unselected package libpng16-16:i386.
Preparing to unpack .../15-libpng16-16_1.6.28-1_i386.deb ...
Unpacking libpng16-16:i386 (1.6.28-1) ...
Selecting previously unselected package libasound2:i386.
Preparing to unpack .../16-libasound2_1.1.3-5_i386.deb ...
Unpacking libasound2:i386 (1.1.3-5) ...
Selecting previously unselected package libfreetype6:i386.
Preparing to unpack .../17-libfreetype6_2.6.3-3ubuntu2.2_i386.deb ...
Unpacking libfreetype6:i386 (2.6.3-3ubuntu2.2) ...
Selecting previously unselected package libfontconfig1:i386.
Preparing to unpack .../18-libfontconfig1_2.11.94-0ubuntu2_i386.deb ...
Unpacking libfontconfig1:i386 (2.11.94-0ubuntu2) ...
Selecting previously unselected package libxfixes3:i386.
Preparing to unpack .../19-libxfixes3_1%3a5.0.3-1_i386.deb ...
Unpacking libxfixes3:i386 (1:5.0.3-1) ...
Selecting previously unselected package libxrender1:i386.
Preparing to unpack .../20-libxrender1_1%3a0.9.10-1_i386.deb ...
Unpacking libxrender1:i386 (1:0.9.10-1) ...
Selecting previously unselected package libxrandr2:i386.
Preparing to unpack .../21-libxrandr2_2%3a1.5.1-1_i386.deb ...
Unpacking libxrandr2:i386 (2:1.5.1-1) ...
Selecting previously unselected package libxtst6:i386.
Preparing to unpack .../22-libxtst6_2%3a1.2.3-1_i386.deb ...
Unpacking libxtst6:i386 (2:1.2.3-1) ...
Selecting previously unselected package teamviewer:i386.
Preparing to unpack .../23-teamviewer_12.0.76279_i386.deb ...
Unpacking teamviewer:i386 (12.0.76279) ...
Setting up libexpat1:i386 (2.2.0-2) ...
Setting up libjpeg62:i386 (1:6b2-2) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu2) ...
Setting up libuuid1:i386 (2.29-1ubuntu2) ...
Setting up zlib1g:i386 (1:1.2.11.dfsg-0ubuntu1) ...
Setting up libsystemd0:i386 (232-21ubuntu3) ...
Setting up libasound2:i386 (1.1.3-5) ...
Processing triggers for bamfdaemon (0.5.3+17.04.20170406-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for libc-bin (2.24-9ubuntu2) ...
Processing triggers for doc-base (0.10.7) ...
Setting up libice6:i386 (2:1.0.9-1) ...
Processing triggers for man-db (2.7.6.1-2) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu5) ...
Setting up libxdmcp6:i386 (1:1.1.2-1.1) ...
Processing triggers for hicolor-icon-theme (0.15-1) ...
Setting up libxau6:i386 (1:1.0.8-1) ...
Setting up libdbus-1-3:i386 (1.10.10-1ubuntu2) ...
Setting up libsm6:i386 (2:1.2.2-1) ...
Setting up libpng16-16:i386 (1.6.28-1) ...
Setting up libfreetype6:i386 (2.6.3-3ubuntu2.2) ...
Setting up libxcb1:i386 (1.11.1-1ubuntu1) ...
Setting up libfontconfig1:i386 (2.11.94-0ubuntu2) ...
Setting up libx11-6:i386 (2:1.6.4-3) ...
Setting up libxrender1:i386 (1:0.9.10-1) ...
Setting up libxdamage1:i386 (1:1.1.4-2) ...
Setting up libxext6:i386 (2:1.3.3-1) ...
Setting up libxfixes3:i386 (1:5.0.3-1) ...
Setting up libxtst6:i386 (2:1.2.3-1) ...
Setting up libxrandr2:i386 (2:1.5.1-1) ...
Setting up libxinerama1:i386 (2:1.1.3-1) ...
Setting up teamviewer:i386 (12.0.76279) ...
Processing triggers for libc-bin (2.24-9ubuntu2) ...
```

Try the following command

```
teamviewer --daemon restart
```

it should pop up a password dialogue box for you to enter you password, then try opening Teamviewer once more.

Does that work ?

---

### Post by Robbyx on 2017-05-10
The password dialogue box did pop up. I filled it in and then clicked on the TV icon. Same error message as in the 1 post above ie The TV daemon is not running. Please start the daemon (needs root permissions) before running TV.

---

### Post by sp40140 on 2017-05-10
@Robbyx
Did you edit init scripts? You do not need to.
I have been using TV for more than 4 years now. Never had issues. And I just did fresh install of 17.04 and installed TV 12. No issues. All you need to do is install the TV deb file using dpkg (as software center doesn't work with third party debs). Re-start the machine. TV shows up as you search for it. Launch it. And you are done with basic set-up. If you want it to run at boot, there is an option in the settings of TV. And it launches TV even before you log in. Very simple set-up.
Looks like something went wrong during install.

---

### Post by Robbyx on 2017-05-10
This time I did not copy the init scripts as suggested in the instructions in comment 1 above. 

I have reinstalled about 5 times each giving the same problem with the daemon. I even looked into the groups and ticked the daemon group. 

I have used TV for a few years with no problems but this time I can not get past start.

Robin

---

### Post by Robbyx on 2017-05-10
Are there any groups  that should be present for TV to work?

Robin

---

### Post by sp40140 on 2017-05-10
```

lrwxrwxrwx 1 root root 40 Mar 23 20:00 teamviewer -> /opt/teamviewer/tv_bin/script/teamviewer
```
No. Nothing special.

---

### Post by Robbyx on 2017-05-10
Thanks, my permissions match yours.

. I am at a loss as to why I can not start teamviewer. I tried to follow their popup advice to get their logs but the command line would not run. 

 Any further ideas to solve the refusal to start?

---

### Post by sp40140 on 2017-05-10
These are the running processes:
```

dell@DELL:/usr/bin$ ps -ef | grep team | grep -v grep
root      2021     1  0 May07 ?        00:02:15 /opt/teamviewer/tv_bin/teamviewerd -d
dell      2536     1  0 May07 ?        00:01:29 /opt/teamviewer/tv_bin/wine/bin/wineserver
dell      2648  2131  0 May07 ?        00:05:15 /opt/teamviewer//tv_bin/TVGuiSlave.64 31 1
dell      2650  2131  0 May07 ?        00:04:49 /opt/teamviewer//tv_bin/TVGuiDelegate 31 1

```
Unfortunately, as I have not run into any issues, I am not experienced with fixing them.
My first instinct is that something went wrong with install. But as you already mention that you have done it multiple times. I got nothing.
But please do let me know if you want to check any set-up / config from my machine.

---

### Post by Autodave on 2017-05-10
Don't know if this will help you or not, but I have always d-led it right from their web page and used *gdebi *to install it. I have it running on 15 machines and never an issue with any of them.

---

### Post by Robbyx on 2017-05-10
Thank you. I have found the solution. 

I decided to login in to Ubuntu as a different admin user. There I found that  TV loaded and was not tripping up over the script. On login It was reporting an error that indicated that TV was already loaded. I was able to restart it and close down normally and then switch back to my usual user name. From there it started with no problem other than it can not find a  connection but that may be to do with a proxy server and I am investigating if that is the cause.

---

### Post by Robbyx on 2017-05-10
I suspect my problem arose because of the way I have set up the group members. I do not really understand how they should be set up.

I have two users: 

**Robin **
Home directory: /home/test
Main group robin 
ID 1001

**test2**
Home: /home/test2
Main group: test2

[B]Main groups:
[/B]
adm: members: robin and test2
robin: members: robin and test2
test: robin 
test2: no members ticked
users: no members ticked

Have I done anything wrong with the setup?

---

### Post by Robbyx on 2017-05-11
I will open a new topic on the user setup.

Thanks for the answers on the TV point

Robin

---

