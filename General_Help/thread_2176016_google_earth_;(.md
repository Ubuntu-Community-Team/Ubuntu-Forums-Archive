---
title: "google earth ;("
date: 2013-09-22
forum: General Help
---

### Post by Frank_Callo on 2013-09-22
I downloaded and installed google earth in a version which is supposed to be linux friendly.  When I try to start it up I get a message saying my video card won't work.  ANyone else run into this.  I'm running ubuntu on a toshiba satalite S3o74 laptop.  Anyone have any thoughts.

---

### Post by oldos2er on 2013-09-22
What video card? Which version of Ubuntu?

---

### Post by m.alaa8 on 2013-09-22
I have the same problem with my Intel 945GME Graphics card. however, the older google earth version is working fine.

---

### Post by Frank_Callo on 2013-09-22
I am using Ubuntu 12.04.3 LTS
here is all the info from the terminal that seems to relate to graphics

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d0300000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at d0400000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, fast devsel, latency 0
    Memory at d0380000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

Thanks.

I am reaping the fruit of the sin of not knowing what is under the hood.  I am seeking atonement.

---

### Post by wheelie207 on 2013-10-17
I upgraded to Ubuntu 13.10 and I can not install Google Earth as it says an error about (ia-32 libs) and the version of Google Earth is 64-bit.
I'm looking for ideas about this problem with the ia-32 error when its a 64-bit software.

I don't know why it removed it from my computer to begin with.

Harold

---

### Post by scouser73 on 2013-10-17
> **wheelie207 said:**
> I upgraded to Ubuntu 13.10 and I can not install Google Earth as it says an error about (ia-32 libs) and the version of Google Earth is 64-bit.
I'm looking for ideas about this problem with the ia-32 error when its a 64-bit software.

I don't know why it removed it from my computer to begin with.

Harold

Hey wheelie207,

I was having the same problems with Google Earth on 13.10 x64, due to ia32-libs no longer being supported but Google Earth relying upon it.  I found a solution on the forum which will enable you and others using x64 systems to install Google Earth.

I know it's a bit of fussing but if you follow each step exactly, you will have Google Earth working again.

Thanks goes to [**[COLOR="#FF0000"]mc4man[/COLOR]**]("http://ubuntuforums.org/member.php?u=320715") for his instructions, I've followed them to the letter and I have Google Earth installed and working perfectly.

**Google Earth Build Package**

Download Google Earth x64 .DEB

Open Terminal, Copy & Paste Following Command And Press Enter

```
sudo apt-get install libc6:i386 lsb-core
```

Open Downloads Folder

Right Click On Google Earth .DEB Package & Select Extract Here

Click On Debian Folder

Right Click on Control & Select Open In Gedit

Remove The Whole Line Containing

**[COLOR="#FF0000"]Depends: lsb-core (>= 3.2), ia32-libs[/COLOR]**

Now Click Save, & Exit Control File

Now Delete The Original Google Earth .DEB Package You Downloaded

Create A Folder called getfix, Now Move The Extracted Google Earth Folder Into The getfix Folder

Now You Are Going To Rebuild The Google Earth .DEB Package

Open Terminal, Copy & Paste Following Command & Press Enter

```
dpkg -b /home/yourname/Downloads/getfix/google-earth-stable_current_amd64
```

Once You Have Done That, Back In Terminal Copy & Paste The Following Command

```
sudo dpkg -i /home/yourname/Downloads/getfix/google-earth-stable_current_amd64.deb
```

The Repackaged Google Earth Will Now Be Installed.

---

### Post by wheelie207 on 2013-10-17
That was great, works perfect. Thanks...
We'll have to pass this info around so others can run google earth.

Harold

---

