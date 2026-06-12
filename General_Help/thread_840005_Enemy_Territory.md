---
title: "Enemy Territory"
date: 2008-06-25
forum: General Help
---

### Post by Jookia on 2008-06-25
I have the linux version of enemy territory on my desktop, I've tried everything I could find, I get the /usr/local/bin or something permission denied error EVEN ON ROOT.

---

### Post by DirtDawg on 2008-06-25
Your post is very vague. At the risk of sounding obvious, you must download the installer file (et-linux-2.55.x86.run). Then open a terminal, make sure you are in the same folder as the ".run" file, and enter this into a terminal to ensure it is executable:
```
chmod +x ./et-linux-2.55.x86.run
```
Then :
```
sudo ./et-linux-2.55.x86.run
```
The installer should run and if you keep everything at default, you should be golden.

NOTE: You should not run the game right away after installing. Close the installer first, then run the game either through the Applications menu or by running 'etwolf' in the terminal. Apparently, if you try to run the game right after installing, you will get permission errors. Maybe this is the root of your problem?

If something goes wrong, post the error message and maybe someone can help you from there.

---

### Post by forger on 2008-06-25
if you run into errors:
[http://katanoon.nl/ubu-e/install.php](http://katanoon.nl/ubu-e/install.php)

---

### Post by Jookia on 2008-06-25
I tried both, and it STILL gives me this..

[img]http://img187.imageshack.us/img187/3130/screenshotjookiaubuntu8sm1.png[/img]

---

### Post by DirtDawg on 2008-06-25
Hmmm, if you ran the script as root (sudo), that is very strange. Have you tried installing it in your Home folder? When it asks you where to install, try entering:
```
/home/<yourUserName>/enemy-territory
```
Other than that, all I can imagine is maybe your installer was corrupted on download? Weird.

BTW, if you do install in your home directory, you'll have to start the game using the 'etwolf' binary file in the enemy-territory directory:
```
~/enemy-territory/etwolf
```

**EDIT**: According to [this post]("http://ubuntuforums.org/showthread.php?t=5246&highlight=enemy+install"), if you run the installer with this command, it may work:
```
su -c "./et-linux-2.60.x86.run"
```

Conversely, according to [this thread]("http://ubuntuforums.org/showthread.php?t=784801&highlight=enemy+install"), if you just hit 'cancel' when the installer asks for your password, it will automatically install the game to your home folder. 

Good luck!

---

### Post by Jookia on 2008-06-25
I've recorded an ogg file of me doing it to clean up any confusion.

I think an error flashed.

```
http://www.mediafire.com/?zms09lb4vtf
```

---

### Post by Marshal0505 on 2008-06-25
excuse me for not reading the entire post but your post reminded me of a comment ....

> 
NOTE: It's important that you exit the installer window and do not press the installers play button. It will cause permission problems for Wolfenstein 

I read on this website [http://gaming.gwos.org/doku.php/guides:64bit:et_wolfenstein](http://gaming.gwos.org/doku.php/guides:64bit:et_wolfenstein)

Starting again and following these instructions to the tee might do it for you (it worked for me).Hope this helps.

---

### Post by DirtDawg on 2008-06-25
> **Jookia said:**
> I've recorded an ogg file of me doing it to clean up any confusion.

I think an error flashed.

```
http://www.mediafire.com/?zms09lb4vtf
```

The error you're getting is because you do not have gtk1.2 installed.
```
sudo apt-get install libgtk1.2
```
but my guess is that has more to do with the installer running in the terminal than it does with your permission errors. 

I would say try the suggestions from my last post. If the "su -c etc...' command doesn't work, you may need to install it in your home folder. I'm not sure what else could be causing the problem, sorry.

---

### Post by Jookia on 2008-06-25
Getting the lib thing worked perfectly.

On the other hand, it was sbin, not bin.

---

### Post by DirtDawg on 2008-06-25
> **Jookia said:**
> Getting the lib thing worked perfectly.

On the other hand, it was sbin, not bin.

Could you please elaborate? Did installing the missing library fix your permission problems?

If the permissions issue is fixed, please explain how and mark the thread as [SOLVED] so others can benefit from the your experiences.

---

### Post by forger on 2008-06-26
> **Jookia said:**
> Getting the lib thing worked perfectly.

On the other hand, it was sbin, not bin.

So you haven't read the whole link I gave you... it clearly stated the necessity of that library

> 
HOWTO: Install RTCW: Enemy Territory and True Combat: Elite
Requirements
For this HOWTO, you will need:

    * Ubuntu 6.06, 5.10 (possibly others)
    * (fast) internet connection

**Step 0: Test your system**
cat /dev/urandom | aplay
This should produce white noise. If it doesn't, something is wrong with your sound set-up. Sound will probably not work in-game.

glxinfo | grep rendering
Should produce 'direct rendering: Yes'. If it doesn't, you will not be able to play. Refer to BinaryDriverHowto to help rectify this.
Step 1: Download RTCW: ET 2.60 installer:
wget [http://ftp.games.skynet.be/pub/wolfenstein/et-linux-2.60.x86.run](http://ftp.games.skynet.be/pub/wolfenstein/et-linux-2.60.x86.run)
Wget automatically saves its progress when it exits. To resume,
wget -c [http://ftp.games.skynet.be/pub/wolfenstein/et-linux-2.60.x86.run](http://ftp.games.skynet.be/pub/wolfenstein/et-linux-2.60.x86.run)

If this link is down, go to Google and find another download location.
**Step 2: Install RTCW: ET**
**[COLOR="Red"]sudo apt-get install libgtk1.2[/COLOR]**
chmod +x et-linux-2.60.x86.run
sudo ./et-linux-2.60.x86.run
Click 'I agree' (twice), then 'Begin install'. Leave all options as defaults. Allow the install to complete, then exit. Do not start the game from the installer.
**Step 3: Test the game**
et
Make sure sound is working, you can find and connect to servers etc.
**Step 4: Fixing sound issues**
If your sound didn't work in Step 3, then try the following:
sudo -s
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
exit

Exit all music players, web browsers etc. then try:
killall esd
et

If you now have sound, then:
sudo -s
echo "echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss" >> /etc/environment
echo "echo "et.x86 0 0 disiable" > /proc/asound/card0/pcm0c/oss" >> /etc/environment
exit
This will save the setting.
**(TC: E) Step 5: Download TC:E files**
Download tcetest_0209_full.zip from somewhere. The TC:E website has a list, if you click 'True Combat: ELITE' in the 'linux' section.
Download tcetest_0.48_update.zip – again, TC:E has several mirrors – you're looking for True Combat:ELITE Patch (ZIP).
**(TC: E) Step 6: Install**
cd //download directory//
sudo mv tcetest_0209_full.zip tcetest_0.48_update.zip -t /usr/local/games/enemy-territory
sudo unzip tcetest_0209_full.zip
sudo unzip -o tcetest_0.48_update.zip
sudo rm tcetest_0209_full.zip tcetest_0.48_update.zip
**(TC: E) Step 7: Play**
et +set fs_game tcetest
**(TC: E) Step 8: Install Maps**
for link in `curl -s [http://www.gamingneelix.de/index.php?action=tcemaps](http://www.gamingneelix.de/index.php?action=tcemaps) |\
grep -o "<a href=\"[^>]*>" | sed -e 's/<[^>]*URL=/ /g' |\
sed -e 's/">$//'`; do wget -c $link; done

This requires curl and wget. If you don't have them, install with
sudo aptitude install wget curl
**(TC: E) Step 9: Create a launcher**
Create a launcher to et +set fs_game tcetest with the icon /usr/local/games/enemy-territory/tcetest/elitelogoicon.ico.


---

