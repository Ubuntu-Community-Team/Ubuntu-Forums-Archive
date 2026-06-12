---
title: "x64 Google Earth"
date: 2014-07-01
forum: General Help
---

### Post by chris-tolley on 2014-07-01
So Google Earth is problematic for 64-bit Ubuntu users.  This happens to be something I figured out using several solutions and mixing them all together.  Since I assume I'm not the only one that has had others solutions not work right the first time, this is my consolidated efforts.  Two users were the prime helpers with this, so credit to them and there information comes first.  Please read all of it before you start smashing buttons in the terminal, as the last bit helps with rebuilding the .deb package.

This comes from [shivanker.goel]("http://askubuntu.com/users/125670/shivanker-goel") on askubuntu.com

[QUOTE=[shivanker.goel]("http://askubuntu.com/users/125670/shivanker-goel")]**1. Repackage old packages**

[COLOR=#333333][FONT=UbuntuRegular]I will use the citrix receiver as an example, but you can use this method for any .deb package:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]First, download the citrix receiver .deb package from their website and make a temporary directory do do the hacking in.[/FONT][/COLOR]
```
[FONT=Ubuntu Mono]mkdir ica_temp[/FONT]
```[COLOR=#333333][FONT=UbuntuRegular]Extract the package[/FONT][/COLOR]
```
[FONT=Ubuntu Mono]dpkg-deb -x icaclient_13.0.0.256735_amd64.deb ica_temp[/FONT]dpkg-deb --control icaclient_13.0.0.256735_amd64.deb ica_temp/DEBIAN
```[COLOR=#333333][FONT=UbuntuRegular]Open the file in gedit (or your favorite editor)[/FONT][/COLOR]
```
[FONT=Ubuntu Mono]sudo gedit ica_temp/DEBIAN/control[/FONT]
```[COLOR=#333333][FONT=UbuntuRegular]Find the line that starts with Depends:.... remove ia32-libs and add lib32z1 lib32ncurses5 lib32bz2-1.0[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Rebuild the modified package[/FONT][/COLOR]
```
[FONT=Ubuntu Mono]dpkg -b ica_temp icaclient-modified.deb[/FONT]
```[COLOR=#333333][FONT=UbuntuRegular]And install it[/FONT][/COLOR]
```
[FONT=Ubuntu Mono]sudo dpkg -i icaclient-modified.deb [/FONT]
[FONT=Ubuntu Mono]sudo apt-get install -f[/FONT]
```[/QUOTE]

Following his guide, I wasn't able to rebuild the package due to errors with the "DEPENDS" line.  That sucked, but made me do some more searching.  

This post from monkeybrain20122[COLOR=#000000] turned out to be the final fix:

[http://ubuntuforums.org/showthread.php?t=2196304&p=12885474#post12885474](http://ubuntuforums.org/showthread.php?t=2196304&p=12885474#post12885474)

He said to remove [/COLOR][COLOR=#000000]dependency ia32-lib.  Tried that, didn't work either.  So I did the next best.  I threw a "#" in front of the depends line, and all was right with the world.  Google Earth opens up like a champ and runs just as it should.  

I hope this helps others that are having the same problem.  [/COLOR]

---

### Post by monkeybrain20122 on 2014-07-01
> **chris-tolley said:**
> [COLOR=#000000]
He said to remove [/COLOR][COLOR=#000000]dependency ia32-lib.  Tried that, didn't work either.  So I did the next best.  I threw a "#" in front of the depends line, and all was right with the world.  Google Earth opens up like a champ and runs just as it should.  

[/COLOR]

It works for me on Ubu13.04, 13.10 and 14.04, all 64 bit, on a few machines. Not sure why and how it didn't work for you.

---

### Post by chris-tolley on 2014-07-01
No idea.  I'm on 14.04, ASUS machine.  Making it disregard the dependency line worked though.  I already had all of the new dependencies, so maybe that had something to do with it...?  Either way, your post to delete the dependency itself is what led to what worked for me.

---

