---
title: "Known bugs and workarounds for edgy"
date: 2006-10-24
forum: General Help
---

### Post by frodon on 2006-10-24
**[SIZE="2"]Disclaimer[/SIZE] :**
[COLOR="Red"]**[SIZE="4"]This is not a support thread, please do not ask for help in this thread.[/SIZE]**[/COLOR]

**This thread aims to list all the known bugs on edgy and provide a workaround to them when it's possible.**

[SIZE="2"][COLOR="Red"]If you're willing to fill a bug report please follow these steps :[/COLOR][/SIZE]
[http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

**- Well known edgy bugs official wiki documentation :**
    * [https://wiki.ubuntu.com/EdgyReleaseNotes?](https://wiki.ubuntu.com/EdgyReleaseNotes?)
    * [https://wiki.ubuntu.com/EdgyKnownIssues](https://wiki.ubuntu.com/EdgyKnownIssues)

**- Nautilus CPU usage jumps to 100% :**
    * Bug report : [https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/54684](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/54684)
    * Workaround : see [this post]("http://ubuntuforums.org/showpost.php?p=1747864&postcount=53") for more informations.
    * **The fix for this bug has been committed to edgy-updates**

**- Azureus from the repositories is broken**
    * Bug report : [https://launchpad.net/distros/ubuntu/+source/azureus/+bug/57875](https://launchpad.net/distros/ubuntu/+source/azureus/+bug/57875)
    * Workaround : [http://ubuntuforums.org/showthread.php?t=144546&highlight=azureus](http://ubuntuforums.org/showthread.php?t=144546&highlight=azureus)

**- Problems with totem-gstreamer and samba shares**
    * Bug report : [https://launchpad.net/distros/ubuntu/+source/totem/+bug/61147](https://launchpad.net/distros/ubuntu/+source/totem/+bug/61147)
    * Workaround : Don't use totem , possible workaround here : [http://www.ubuntuforums.org/showthread.php?t=315333](http://www.ubuntuforums.org/showthread.php?t=315333)

**- Ubuntu logo stretched up on widescreen**
    * Bug report : [https://launchpad.net/distros/ubuntu/+source/usplash/+bug/64147](https://launchpad.net/distros/ubuntu/+source/usplash/+bug/64147)
    * Workaround : none for the moment

**- Generic kernel don't boot**
    * Bug report : [https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/67256](https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/67256)
    * Workaround : [http://ubuntuforums.org/showthread.php?t=282956](http://ubuntuforums.org/showthread.php?t=282956)

**- Flash plugin causes firefox crash**
    * Bug report : [https://launchpad.net/distros/ubuntu/+source/firefox/+bug/14911](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/14911)
    * Workaround : [http://ubuntuforums.org/showpost.php?p=1673725&postcount=23](http://ubuntuforums.org/showpost.php?p=1673725&postcount=23)

**- Keyboard random repeat and dropped key presses**
    * Bug report : [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39315](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39315)
    * Workaround : Fixed

**- KDE Screen power saving settings aren't reloaded after reboot**
    * Bug report : [https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/65791](https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/65791)
[https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/66215](https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/66215)
    * Workaround : [http://ubuntuforums.org/showthread.php?p=1819397](http://ubuntuforums.org/showthread.php?p=1819397)

**- Computer freezes sometimes with skype 1.3**
    * Bug report : [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/53216](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/53216)
    * Workaround : Use the 1.2 version instead.

**- DMRAID don't work**
    * Bug report : [https://launchpad.net/distros/ubuntu/+source/dmraid/+bug/54246](https://launchpad.net/distros/ubuntu/+source/dmraid/+bug/54246)
    * Workaround : On going.
    * Post to read : [http://ubuntuforums.org/showpost.php?p=1796784&postcount=72](http://ubuntuforums.org/showpost.php?p=1796784&postcount=72)

**- Update from dapper to edgy for those who used the quinns repository and installed Xgl/compiz at the time :**
    * You may need to downgrade some libraries (such as libcairo, libmesa, ...) to the dapper version to avoid conflicts during the upgrade. If you used this repository at the time and installed compiz i advice you to do the update through synaptic thus you will see which library create the conflict.

This is just a start, so everyone is welcome to report **known edgy bugs** or workarounds in this thread

---

### Post by ubuntu_demon on 2006-10-24
nice work!

Here's one to add :
[https://wiki.ubuntu.com/EdgyKnownIssues](https://wiki.ubuntu.com/EdgyKnownIssues)

---

### Post by finalbeta on 2006-10-24
Some bugs that make Totem less usable.

- Totem no longer plays files from windows shares.
- Many streams that used to play with totem no longer play. (They just show the first frame)
- Totem does not stop the screen saver from starting when playing a movie in full screen.
- Totem freezes when trying to play .sub files. (When .sub files are inside the totem dir)
* Bugreports : [https://launchpad.net/distros/ubuntu/+source/totem/+bug/61147](https://launchpad.net/distros/ubuntu/+source/totem/+bug/61147) , [http://bugzilla.gnome.org/show_bug.cgi?id=360537](http://bugzilla.gnome.org/show_bug.cgi?id=360537) , [http://bugzilla.gnome.org/show_bug.cgi?id=361571](http://bugzilla.gnome.org/show_bug.cgi?id=361571)
[http://bugzilla.gnome.org/show_bug.cgi?id=364560](http://bugzilla.gnome.org/show_bug.cgi?id=364560)
* Workaround: Don't use Totem / Gstreamer

---

### Post by tormod on 2006-10-24
> **ubuntu_demon said:**
> nice work!

Here's one to add :
[https://wiki.ubuntu.com/EdgyKnownIssues](https://wiki.ubuntu.com/EdgyKnownIssues)
Wouldn't it be better to have everything in one place? What is the motivation for this thread when we already have [Please contribute to Edgy Known Issues]("http://ubuntuforums.org/showthread.php?t=280231") ?

---

### Post by frodon on 2006-10-25
This thread aims to provides a clear list of well known bugs with workarounds and will be transfered in the edgy support section once edgy will be released.
To be quick the goal is to find quickly known bugs and workarounds for edgy without browsing a whole thread.

---

### Post by tormod on 2006-10-25
> **frodon said:**
> This thread aims to provides a clear list of well known bugs with workarounds and will be transfered in the edgy support section once edgy will be released.
To be quick the goal is to find quickly known bugs and workarounds for edgy without browsing a whole thread.

That sounds exactly like the goal of "EdgyKnownIssues" :)

---

### Post by chefweb on 2006-10-25
"- Problems with totem-gstreamer and samba shares
* Bug reports : [https://launchpad.net/distros/ubuntu...tem/+bug/61147](https://launchpad.net/distros/ubuntu...tem/+bug/61147)
* Workaround : Don't use totem-gstreammer, maybe totem-xine instead "

Streaming from samba or ftp doesn't work with totem-gstreamer or totem-xine .. this bug is very infuriating :-k

---

### Post by beerfan on 2006-10-26
> **chefweb said:**
> Streaming from samba or ftp doesn't work with totem-gstreamer or totem-xine .. this bug is very infuriating :-k

Does gstreamer support avahi/zeroconf? I just set up avahi and mt-daapd on dapper and it has solved my grief with samba and mp3s.

---

### Post by Viper023 on 2006-10-26
after i have installed edgy, if i go to System - Administration , the Disks icon is no longer there?  Is there a workaround to this?

logan

---

### Post by hotani on 2006-10-26
Please tell me there is a workaround for Edgy knocking me down to 1 core on a dual core chip?

---

### Post by mjziegle on 2006-10-26
I'm coming from dapper so when I upgraded gnome broke.  Specifically it was the DRI portion of the ati (fglrx) driver.  I kept getting kicked back to the login after the upgrade.    

To fix:  After upgrading make sure to add 

Section "Extensions"

	Option "Composite" "0"

EndSection

to the end of xorg.conf and then run

sudo aticonfig --overlay-type=Xv

Fixed my problems.  Should fix the getting kicked back out problem.

---

### Post by chippy99 on 2006-10-26
If you have a Matrox graphics card you will have to revert to the vesa driver the mga driver seems to be broken. Get an error on monitor that refresh rate is out of range.

---

### Post by alphamerik on 2006-10-27
openafs-modules-source will not build in Edgy.

Bug reported here:
[https://launchpad.net/distros/ubuntu/+source/openafs/+bug/68526](https://launchpad.net/distros/ubuntu/+source/openafs/+bug/68526)

Issue first seen here:
[http://ubuntuforums.org/showthread.php?t=281756&highlight=openafs+edgy](http://ubuntuforums.org/showthread.php?t=281756&highlight=openafs+edgy)

Solution:
If you are brave download OpenAFS 1.4.2 source and try to compile/install yourself.

---

### Post by alphamerik on 2006-10-27
Another issue I experienced during upgrade from dapper:

Some X fonts had disappeared - specifically, I had some custom font specifications in .emacs.  Emacs would start with an error that the fonts were not valid and would display blocks instead of letters.  
Font would not render when using 'xfontsel', but would appear as available.

The solution:
Type 'xset fp rehash' in a terminal to recreate the font database.

---

### Post by elettronicha on 2006-10-27
Ubuntu splashscreen is stretched for widescreen: [https://launchpad.net/distros/ubuntu/+source/usplash/+bug/64147](https://launchpad.net/distros/ubuntu/+source/usplash/+bug/64147)
No workarounds at the moment.

---

### Post by ckempo on 2006-10-27
> **hotani said:**
> Please tell me there is a workaround for Edgy knocking me down to 1 core on a dual core chip?

Install the -generic kernel rather than the -i386 one. My dual core is working fine, both cores showing in System Monitor.

---

### Post by hotani on 2006-10-27
Don't want to derail this fine thread, and there is another one discussing  how the [generic kernel won't boot some systems, and the 386 kernel doesn't do 2 cores](http://www.ubuntuforums.org/showthread.php?t=285272). We're still not sure if it is nvidia driver related or something in fstab that the generic kernel is not happy about. Either way, an updated FIXED generic kernel would be reeeeally nice.

---

### Post by Tor M on 2006-10-27
Hi!
I don`t know if this is a general bug or just on my machine. I have a laptop with an ATI X700 graphics card, that makes the computer boot with a black screen aka the known bug in post 1.
When I try to boot the cd in safe graphical mode edgy still tries to load the ati driver and not the vesa driver as dapper did.
Because of this my machine boots in to a black screen even if I try to boot in "safe mode". I have to manually edit xorg.conf and restart X to get the vesa driver to load.
Have anybody else experienced this bug?

Tor Martin

---

### Post by frodon on 2006-10-27
Please report here only **known bugs** or even better bugs confirmed in launchpad with the link, otherwise this thread won't serve its purpose.

Thanks

---

### Post by graigsmith on 2006-10-27
when is the nautilus problem gonna be fixed?  also after the nautilus problem the only way i could log back in was to restart the computer.  

im not gonna be happy if there is no update for nautilus.  cause ill definately have to uninstall it from my computer, and my mom's

---

### Post by frodon on 2006-10-27
Nautilus problem is solved by opening the system monitor and killing nautilus, no need to reboot. But it's damn annoying indeed.

---

### Post by elettronicha on 2006-10-27
> **frodon said:**
> Please report here only **known bugs** or even better bugs confirmed in launchpad with the link, otherwise this thread won't serve its purpose.

Thanks
It's better you underline that in your first post, in my opinion. ;)

---

### Post by distortedstar on 2006-10-27
*I already posted this in the normal threads, but was it was getting pushed down since there's really no need to reply to it. I thought it would be more appropriate here.*

I was sorely dissapointed when Flash caused Firefox to crash on my brand new Edgy install, but after some searching I found a solution that solved the problem for me:

In the /etc/firefox/firefoxrc file, insert this line:
Code:

export XLIB_SKIP_ARGB_VISUALS=1

I've also seen a couple more solutions that may work for you, if this doesn't:

1. Comment out the composite section in x.org
2. Change your color depth to 24 bit, if you haven't already

Hope this post helps out some other frustrated people!

Launchpad bug discussion:
[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/14911](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/14911)

---

### Post by graigsmith on 2006-10-27
Are they going to patch this problem? or are we stuck with killing nautilus over and over?  my parents are not skilled enough to kill a nautilus task.

---

### Post by frobroj on 2006-10-28
Anyone know whats up with "VI"? I cant get the arrow keys to work. When I edit in VI the arrow keys output alpha characters and carriage returns. Any Ideas?

Thanks

---

### Post by frobroj on 2006-10-28
Found the fix... [http://ubuntuforums.org/showthread.php?t=269787](http://ubuntuforums.org/showthread.php?t=269787)

So whats the deal in all other ubuntu revisions it worked without installing vim-full. Why the change? Oh well at least I can get some work done.
:-k

---

### Post by handy on 2006-10-28
The following is a known bug, with multiple reports.

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39315](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39315)

There seems to be more than one problem causing this one though:-

[I]My keyboard timing is out, it seems to lag & then race, which causes lots of duplicated letters & some missed ones.

I tried unsuccessfully to solve it in the Repeat Keys dialog & ended up turning Repeat Keys off.

I have tried 3 different keyboards to no avail?

My motherboard is a Gigabyte GA-K8ns Ultra-939 with 64bit 3500 AMD CPU. (my signature has all the spec's)[/I]

**[Edit:] *I have found over the past 3 weeks that my USB mouse will not work on a reboot (approx 1 out of 3 times), also sometimes the whole boot process hangs forever very early in the Edgy boot graphic.***

---

### Post by handy on 2006-10-28
> **Viper023 said:**
> after i have installed edgy, if i go to System - Administration , the Disks icon is no longer there?  Is there a workaround to this?

logan

**pysdm** in the repo's.

[This link if you are interested?]("http://ubuntuforums.org/showthread.php?t=285279")

---

### Post by jdunn on 2006-10-28
I Can't set DPMS (Screen Power Save) Standby/Suspend/Off times correctly on a fresh install of  Kubuntu Edgy.  Any changes I make in 'System Settings->Monitor&Display->Power Saving' always revert to '5 hours'.  I can make DPMS work at the command prompt with 'xset' (example: xset dpms 0 0 1800) but I haven't figured out how to automate this.

---

### Post by Sal Z on 2006-10-29
There are missing Dependancies for cinepaint , specifically seems that libgutenprintui1-1 is missing from the official repositories.

Possible workaround: install libgutenprintui1-1 from 
[http://packages.debian.org/unstable/libs/libgutenprintui1-1](http://packages.debian.org/unstable/libs/libgutenprintui1-1)

---

### Post by rbmorse on 2006-10-29
Kdar is missing libdar3c2a, nor is it in the repositories. This is not a big problem unless all you backups are done in dar...then it's quite serious.

---

### Post by hotani on 2006-10-29
RE: the azureus problem - people in [this thread](http://www.ubuntuforums.org/showthread.php?t=276211) have had success by downloading the .jar from the azureus site and replacing the existing one.

> **duhblow7 said:**
> Here is what solved it for me.

Go to [http://azureus.sourceforge.net](http://azureus.sourceforge.net) and download the newest jar.

Copy the downloaded jar file over your current Azureus2.jar (mine was located at /usr/share/java/Azureus2.jar

Open Azureus again and it should open without problems.

---

### Post by krismatth3 on 2006-10-29
Problem booting with samba shares in /etc/fstab, I first witnessed this in edgy:

[http://ubuntuforums.org/showthread.php?t=286889&highlight=samba+fstab](http://ubuntuforums.org/showthread.php?t=286889&highlight=samba+fstab)

---

### Post by Enigmatic on 2006-10-29
I reported a bug where files transfers to XFS partitions/drives via Nautilus caused very slow transfer speeds, but via commandline work just fine:

[https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/68858](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/68858)

---

### Post by hexion on 2006-10-29
I've made a workaround for LIRC problem in Edgy.

Here is the HOWTO. It solves the problem in some easy steps.
[http://www.ubuntuforums.org/showthread.php?p=1684737#post1684737](http://www.ubuntuforums.org/showthread.php?p=1684737#post1684737)

Please, add it to the wiki.

---

### Post by jdunn on 2006-10-29
My Audio/Video is out of Sync in Kaffeine when playing DVDs.  Never had this problem in Dapper but I have it in Edgy.  It seems to be an issue with libxine 1.1.2 that effects Kaffeine and other front-end players.

Bug Tracking
[http://sourceforge.net/tracker/index.php?func=detail&aid=1544349&group_id=9655&atid=109655](http://sourceforge.net/tracker/index.php?func=detail&aid=1544349&group_id=9655&atid=109655)

TEMPORARY solution in Kaffeine is to select Video->Video Settings->Offset every time you play a DVD.  I usually have to adjust the offset by 150ms

---

### Post by hotani on 2006-10-30
I am having the [same problem](http://www.ubuntuforums.org/showthread.php?t=287439) in gxine when viewing DVDs and some videos.

---

### Post by elettronicha on 2006-10-30
**BUG**
**KDE Screen power saving settings** aren't reloaded after reboot:
[https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/65791](https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/65791)
[https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/66215](https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/66215)

Workarounds: none that I know.

---

### Post by SugarAddicted on 2006-10-30
about the nautilus 100% cpu usage...this looks like not to be an edgy bug because fedora core 6 has it as well ...so looks like its a gnome bug...

the only workaround i found is this...Go to the folder that is causing you trouble and change the Folder View from " View as icons to -> View as list"
kill nautilus with killall nautilus and there you go no problem anymore...

this doesn't fix the problem when you're downloading a file...//:cry:  

(this bug happens to my machine when i'm converting music files or downloading some file from web and i have to go into the specific folder to view its contents)

hope it helps and waiting for a fix

---

### Post by jdunn on 2006-10-31
> **elettronicha said:**
> **BUG**
**KDE Screen power saving settings** aren't reloaded after reboot:
[https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/65791](https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/65791)
[https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/66215](https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/66215)

Workarounds: none that I know.

I started KDE bug tracking on it [http://bugs.kde.org/show_bug.cgi?id=136542](http://bugs.kde.org/show_bug.cgi?id=136542)  
feel free to add your comment to the tracker.

---

### Post by brt on 2006-11-01
BUG: Skype lets the system freeze for 30s or more on incoming chats
possible Workaround(s): disable soundevent on incoming chats
or:
some user reported to make it work after deinstalling the .deb package and installing the static-qt-binary version

skype developers state that the bug is kernel related. some say its related to the alsa drivers together with smp. 

[https://launchpad.net/distros/ubuntu/+bug/58194](https://launchpad.net/distros/ubuntu/+bug/58194)
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/53216](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/53216)

some users also state this beeing a DoS vulnerability!

---

### Post by frodon on 2006-11-03
> **brt said:**
> BUG: Skype lets the system freeze for 30s or more on incoming chats
possible Workaround(s): disable soundevent on incoming chats
or:
some user reported to make it work after deinstalling the .deb package and installing the static-qt-binary version

skype developers state that the bug is kernel related. some say its related to the alsa drivers together with smp. 

[https://launchpad.net/distros/ubuntu/+bug/58194](https://launchpad.net/distros/ubuntu/+bug/58194)
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/53216](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/53216)

some users also state this beeing a DoS vulnerability!Yes it's a damn annoying bug, i still use the 1.2 version due to this annoying bug.
Added in the list

---

### Post by Sokraates on 2006-11-05
BUG: Audio-CDs no longer mount after yesterday's (kernel)update.

[https://launchpad.net/distros/ubuntu/+bug/70434](https://launchpad.net/distros/ubuntu/+bug/70434)

Here's the workaround (also found in the bug-report):

"*The workaround with Kubuntu is pretty easy: in the app (tried it with KsCD or KAudioCreator) you need to select /dev/hd* or media:/hd* instead of the default /media/cdrom*.*"

---

### Post by bpang on 2006-11-05
If you've upgraded to Edgy and suddenly you are having trouble with USB devices.

Kernels => 2.6.16 have a feature that checks whether devices can be given as much power as they claim to need. If there's not enough power, the device is not activated.

[http://ubuntuforums.org/showthread.php?t=285873](http://ubuntuforums.org/showthread.php?t=285873)
[http://lists.debian.org/debian-kernel/2006/07/msg00506.html](http://lists.debian.org/debian-kernel/2006/07/msg00506.html)

My dmesg was returning the following when I plugged in a device to an unpowered hub:
no configuration chosen from 1 choice

This work-arounds in the linked posts worked for me. Hope this helps others. It took me days to find the answer.

---

### Post by anewbie on 2006-11-07
There is a known bug with some tv tuner not producing sound. This was due to a rewrite of a driver which is in 2.16.17-10. The fix is to upgrade to a kernel newer than 2.16.18-3.

Haven't tested the fix yet but tracked down the author of the rewrite who confirmed the issue. If edgy doesn't upgrade to a newer kernel in a week or two i'll probably take a stab at manually building/installing a newer kernel.

---

### Post by johnnymac on 2006-11-07
May wanna throw this one in the mix...Dang ptp camera issue...

[http://www.ubuntuforums.org/showthread.php?t=290205](http://www.ubuntuforums.org/showthread.php?t=290205)

---

### Post by mmangus on 2006-11-08
> **alphamerik said:**
> openafs-modules-source will not build in Edgy.

Bug reported here:
[https://launchpad.net/distros/ubuntu/+source/openafs/+bug/68526](https://launchpad.net/distros/ubuntu/+source/openafs/+bug/68526)

Issue first seen here:
[http://ubuntuforums.org/showthread.php?t=281756&highlight=openafs+edgy](http://ubuntuforums.org/showthread.php?t=281756&highlight=openafs+edgy)

Solution:
If you are brave download OpenAFS 1.4.2 source and try to compile/install yourself.

While it's true there are problems between openafs-1.4.1 and some kernels (i.e. 2.6.17.x) there is method to build openafs-1.4.2 kernel module under edgy (kernel 2.6.17.x) in an easy way (i.e. using module-assistant tool).

The trick is to replace openafs.tar.gz (installed in /usr/src/ by openafs-modules-source) with a slightly changed stock openafs-1.4.2.tar.gz, and proceed with "module-assistant ..." commands.

Here "slightly changed" basically means that stock tar.gz need:
- a debian subdirectory (to build debian package)
- debian changes for kernel module build
Nothing else. I've tested this method for an Edgy with kernel 2.6.17-10-386 and it works. I think should work for others kernels/architecture (as amd64) as well.

If someone needs a more detailed list of steps or an howto... please write to me at:
  marco -- a t -- printk -- d o t -- it

HTH
Regards,
-- Marco

---

### Post by cormega on 2006-11-08
my edgy freezes after a few mins of surfing online. at first i thought it was firefox that did it, so i tried opera but no luck. then i thought it might be some sites i surfed with lots of heavy flash & shockwave content etc but it happens all the time. even while surfing these forum pages which are fairly light in content , the crash occured 4 times!

i am running edgy on a dell inspiron 1705 core 2 duo 2.16 ghz 2 gb ram.
had the same problem on dapper when running the 686-smp kernel for dual core support so i am pretty sure it is related to the core 2 duo processor in some way.

anyone heard of this before or know a fix ?

---

### Post by ser1alsn1per on 2006-11-10
> **hotani said:**
> Please tell me there is a workaround for Edgy knocking me down to 1 core on a dual core chip?

first off why do you want go back to 1 core 


possibly using grub to boot to your 1 core setting or remove smp k7


if you have amd that is 

hope it helps

---

### Post by Pcghost on 2006-11-10
I'm pretty sure he means that he/she is unable to run the smp kernel without freezes, as I too am suffering this.  Edgy + SMP kernel + Nvidia driver = frozen PC.  The only way I can run edgy successfully is to use the i386 kernel.  Anyone know why?

---

### Post by elettronicha on 2006-11-10
[HAL doesn't work properly on Asus M6Ne]("https://launchpad.net/distros/ubuntu/+source/hal/+bug/64838")
Bug #64838 : no battery/lid reported on ASUSTeK M6Ne
And the gnome-power-manager (or KDE-power-manager) doesn't recognize battery states. It's critical to me, but it seems none cares of that bug.

---

### Post by konradsa on 2006-11-12
BUG: ACPI events turn on backlight of a blanked screen

[https://bugzilla.novell.com/show_bug.cgi?id=197858](https://bugzilla.novell.com/show_bug.cgi?id=197858)

Workaround: Use 	
```

Option       	"NoPM" "yes"
```

in ServerLayout section of xorg.conf (described in link).

---

### Post by dpm on 2006-11-12
> **frodon said:**
> 

**- Nautilus CPU usage jumps to 100% :**
    * Bug report : [https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/54684](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/54684)
    * Workaround : none


Looking at the latest comments on the bug report, there is a workaround. The bug was fixed upstream and Sebastien Bacher backported the patch and made the packages available at:

[http://people.ubuntu.com/~seb128/debug/54684/]("http://people.ubuntu.com/%7Eseb128/debug/54684/")

It seems that the packages might be officially backported at some point, but there is no concrete information about this.

I just thought that the intitial post of this thread could be updated with this information.

Cheers.

---

### Post by frodon on 2006-11-13
Updated ;)

I took your post has reference.

Thanks for the update.

---

### Post by dpm on 2006-11-13
> **frodon said:**
> Updated ;)

I took your post has reference.

Thanks for the update.

Thank you!

---

### Post by TheForkOfJustice on 2006-11-14
My desktop computer will not reboot with Ubuntu Edgy installed (fresh from CD). Instead, it will unload like it is supposed to and instead of rebooting, the fans inside start going at full blast. I have to hold down the button to shut the computer down and then reboot it.

ALSO my SECOND hard drive sounds a little...ODD...when I write to it. Not only the 'sound' but also the length of time it takes to write. I was transferring a 700MB iso file but it still seemed to take longer than it should to move. It could be just me but that was my impression.

I am able to run Edgy fine, though. Looks nice. It's just the rebooting that needs fixing here.

I have an HP Pavillion a420n. K7 processor.

My lspci output:

> 00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Communication controller: Agere Systems LT WinModem (rev 02)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78 )
01:00.0 VGA compatible controller: nVidia Corporation NV31 [GeForce FX 5600] (rev a1)
ALSO:

The gparted software on your installation CD is messed up. For some reason when I repartition manually and reformat, the parts I change have a good chance of not showing up as formatted when I go to the next screen. I had to use the Gparted LiveCD from Sourceforge to partition everything right.

As long as I don't touch the partitions with your included gparted software then installation continues fine and dandy.

EDIT

[http://www.ubuntuforums.org/showthread.php?t=287319&highlight=edgy+reboot](http://www.ubuntuforums.org/showthread.php?t=287319&highlight=edgy+reboot)

I had the same problem as this guy. The LiveCD didn't want to reboot after installation   either. And now the installed version doesn't want to reboot (and possibly shut down) by itself.

EDIT EDIT

Edgy is eating my XFS partitions! It appears there are more partition-detecting problems than the one in the installer.

I  SUGGEST NOT USING XFS, at least the ext3 seem to be detected fine (even though the new ext3 partitions I made in the installer couldn't be detected by the installer). This may be related to the ugly noises I heard coming from my second hard disk that I mentioned at the beginning of this post.

---

### Post by mdurham on 2006-11-19
> **desp said:**
> Looking at the latest comments on the bug report, there is a workaround. The bug was fixed upstream and Sebastien Bacher backported the patch and made the packages available at:

[http://people.ubuntu.com/~seb128/debug/54684/]("http://people.ubuntu.com/%7Eseb128/debug/54684/")

It seems that the packages might be officially backported at some point, but there is no concrete information about this.

I just thought that the intitial post of this thread could be updated with this information.

Cheers.
What exactly should be done with the 6 debs? Install them all or what? Does this fix nautilus hogging the cpu?
Cheers Mike

---

### Post by Davidios on 2006-11-19
There is a little problem with nautilus:

[#69665]("https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/69665")

---

### Post by ILIJA on 2006-11-19
sweet, nice work! :)

---

### Post by handy on 2006-11-19
I posted my problems in #27 of this thread 3 weeks ago.

Edgy has it's nice features, but I can not live any longer with a poorly operating keyboard & mouse.

I am typing this from Dapper, it is good to be home!

---

### Post by tormod on 2006-11-20
As a possible workaround for some hardware issues, I would suggest installing the feisty 2.6.19 kernel on your edgy install. The kernels are pretty much backwards compatible between releases, in the way that the Edgy kernel runs fine on Dapper as well.

To do this, change to feisty in **/etc/apt/sources.list** (it's usually enough to change the first line only), **sudo apt-get update**; **sudo apt-get install linux-image-2.6.19-6-generic** (the -6- is the current one right now - check with **apt-cache search linux-image-2.6.19**). Afterwards change back to edgy in **sources.list** and run **sudo apt-get update** before you do any more updates!

You will then have both 2.6.17 and 2.6.19 installed and you can choose between them at boot.

---

### Post by BoredByPolitics on 2006-11-20
(Edgy) Laptop lid being closed/opened causes a sig11 crash in X, apparently caused by the acpi monitoring aspect of X.  Solution is to disable acpi monitoring in X:

[http://ubuntuforums.org/showthread.php?t=284872](http://ubuntuforums.org/showthread.php?t=284872)

---

### Post by iLoVe.cF- on 2006-11-21
I got one bug..

My comp

Radeon x800xl/x800xt/x800gto/x850xtpe same problem on all @ my place for all. havnt tried anyother cards..

But my boot screen is in black n white :S

How to install new ? i want the real one =)

---

### Post by IanW on 2006-11-21
You're probably using the 64-bit build?

There's a known bug in the 64-bit usplash, a b&w bootscreen _is_ the workaround.

---

### Post by randysparks on 2006-11-21
Edgy seems to be chronically buggy. I'm turning up many, many bugs. I would advise everybody to avoid it and use Dapper (6.06).  

What are the changes of them releasing a second ISO release, like they did for Dapper? ie. 6.10.01? Or was that only done because Dapper is LTS? 

Bearing in mind that the openSUSE guys released a "remastered" version of 10.1, because of some show-stopping bugs, it's starting to seem that these 6 month release cycles are too aggressive.

---

### Post by tormod on 2006-11-21
> **randysparks said:**
> Edgy seems to be chronically buggy. I'm turning up many, many bugs. I would advise everybody to avoid it and use Dapper (6.06).It works very nicely for many people. I would advise people to try out the live CD thoroughly first, and if everything works fine, proceed to installation. And keep a backup of Dapper...

> What are the chances of them releasing a second ISO release, like they did for Dapper? ie. 6.10.01? Or was that only done because Dapper is LTS?Yes, 6.06.1 happened only because it is an LTS. But many things will be fixed in edgy-updates and edgy-backports. Even installation bugs can be fixed, since you can update the installer before starting it, when you use the live Desktop CD.

> Bearing in mind that the openSUSE guys released a "remastered" version of 10.1, because of some show-stopping bugs, it's starting to seem that these 6 month release cycles are too aggressive.Especially this 4-month release was a little... edgy. But we love all the new, fresh software don't we :)

---

### Post by frodon on 2006-11-21
> **randysparks said:**
> Edgy seems to be chronically buggy. I'm turning up many, many bugs. I would advise everybody to avoid it and use Dapper (6.06).  

What are the changes of them releasing a second ISO release, like they did for Dapper? ie. 6.10.01? Or was that only done because Dapper is LTS? 

Bearing in mind that the openSUSE guys released a "remastered" version of 10.1, because of some show-stopping bugs, it's starting to seem that these 6 month release cycles are too aggressive.The "if it don't work for me it won't work for you" kind of arguments are useless, edgy work really well for many of us so advicing people to not use edgy base on your sole experience is pointless.

Further post like this will be removed or move elsewhere if some of you are willing to debate on this.

**[SIZE="3"]Please keep this thread on topic now[/SIZE]**, thanks.

---

### Post by iLoVe.cF- on 2006-11-21
you probaly running 64 bit edgy..
Answer: YES( and love it.)

i got actually less problems in 64 bit.. :O only thing that is a real pain in the a¤¤ is the damn no flash support (nearly) :'(

hmm.. well.. you shudnt avoid edgy..

it should come another iso release..

Another bug btw..

Using xmms,gaim and install running live cd crashes on my amd 64 in edgy 64 bit dvd and i386 dvd

Its worse on the 64 bit dvd

but on normal cd.. no problems at all :O

but the boot flash screen.. tnx for the b&w.. gimme some extra info ?

Since i got not much time.. and dont got like all day everyday anymore.. got alot of exams now.. norwegian exam in 2 days.. wooh.. nah..

Well.. got an url.. and u'd be my angel :D ( not in gay way) xD

---

### Post by pixelpusher on 2006-11-23
VMware server console fails to start ... for me removing libdbus-1-2 made the difference...

apt-get remove libdbus-1-2

(this assumes you have libdbus-1-3 installed)
Other references suggest running 

LD_PRELOAD=/usr/lib/libdbus-1.so.3:$LD_PRELOAD vmware

---

### Post by chrisccoulson on 2006-11-23
Has anyone mentioned DMRAID not working with the Edgy kernel, meaning onboard FakeRAID arrays don't work?

See [https://bugz.launchpad.net/distros/ubuntu/+source/dmraid/+bug/54246]("https://bugz.launchpad.net/distros/ubuntu/+source/dmraid/+bug/54246").

There seems to be an updated DMRAID package on lauchpad, but it's not in the repositories. This is the only thing stopping me from upgrading to Edgy, as I currently run from a striped array using DMRAID.

---

### Post by tormod on 2006-11-23
> **chrisccoulson said:**
> Has anyone mentioned DMRAID not working with the Edgy kernel, meaning onboard FakeRAID arrays don't work?

Your link is broken: [https://launchpad.net/bugs/54246](https://launchpad.net/bugs/54246)

Given that dmraid never was officially supported nor worked in the installer, this is hardly a regression, but I certainly hope it will be fixed soon anyway.

FWIW, I wrote up my experience on installing 6.10 on a fakeraid:
[https://wiki.ubuntu.com/FakeRaidEdgy](https://wiki.ubuntu.com/FakeRaidEdgy)

Tormod

---

### Post by Drew Woodard on 2006-11-23
> **chrisccoulson said:**
> Has anyone mentioned DMRAID not working with the Edgy kernel, meaning onboard FakeRAID arrays don't work?

See [https://bugs.launchpad.net/distros/ubuntu/+source/dmraid/+bug/54246]("https://bugs.launchpad.net/distros/ubuntu/+source/dmraid/+bug/54246").

There seems to be an updated DMRAID package on lauchpad, but it's not in the repositories. This is the only thing stopping me from upgrading to Edgy, as I currently run from a striped array using DMRAID.



small typo in the launchpad link.

chrisccoulson is right, this should be in the list as it's pretty severe.  Someone doing an upgrade from dapper to edgy on a machine with an existing software raid could experience significant lost time reconstructing their array, or worst case, data loss.  As is discussed in the launchpad bug report and in this discussion:
[http://ubuntuforums.org/showthread.php?t=286066](http://ubuntuforums.org/showthread.php?t=286066)

---

### Post by frodon on 2006-11-23
First post updated with this bug report.

Thanks for the report ;)

---

### Post by tormod on 2006-11-23
- Nautilus CPU usage jumps to 100%
This has now been fixed in edgy-proposed (and soon in edgy-updates).

---

### Post by frodon on 2006-11-23
Nice, my CPU will love the update lol

---

### Post by stenrulz on 2006-11-25
check out [stenrulz.coms ]("http://stenrulz.wetpaint.com")forum to access go to our links, Forums!!

---

### Post by lotusleaf on 2006-11-27
Anyone using Edgy, especially Kubuntu Edgy, please confirm this bug for KDar:

[https://bugs.launchpad.net/distros/ubuntu/+source/kdar/+bug/62699](https://bugs.launchpad.net/distros/ubuntu/+source/kdar/+bug/62699)

When I try to install kdar on Kubuntu Edgy, I receive the following message:

```
kdar:

  Depends: libdar3c2a  but it is not installable
```

So far a few others have confirmed this, I'm sure everyone running Kubuntu Edgy will notice this too if they try to install kdar, so please, let's get this confirmed and brought attention to so it can be fixed, because libdar3c2a currently doesn't exist for Edgy, thus kdar does not install. I believe this issue was also lightly mentioned within this very thread.

I mentioned this in #kubuntu-devel.

Anyone running Edgy, if you have time, please check this for yourself, and confirm if when you try installing kdar it spits out this same error as I mentioned above, thank you for reading.

Edit: hopefully this one will be fixed soon:

> <allee> lotusleaf: I've added kubuntu-team to kdar bug subsciptor.  So hopefully such bug don't slip through unnoticed in the future

---

### Post by Somenoob on 2006-11-27
known workarounds for lags that appears out of nowhere?

---

### Post by Drew Woodard on 2006-12-01
> **Somenoob said:**
> known workarounds for lags that appears out of nowhere?

can you be more specific, is it audio, screen drawing, mouse cursor, something else?

---

### Post by hoagie on 2006-12-03
I think nobody mentioned this bug of open office base. [https://bugs.launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/73395](https://bugs.launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/73395)
Please people confirm this bug so it gets fixed. It's a major bug about the for wizard no being able to finish a form.

---

### Post by nexu56 on 2006-12-09
> - Problems with totem-gstreamer and samba shares
* Bug report : [https://launchpad.net/distros/ubuntu...tem/+bug/61147](https://launchpad.net/distros/ubuntu...tem/+bug/61147)
* Workaround : Don't use totem 

That workaround is incorrect - it affects all players.

[Here is the real workaround.]("http://www.ubuntuforums.org/showthread.php?t=315333")

---

### Post by TrendyDark on 2006-12-11
I'm not sure if this is a problem in Edgy or just something I ran into, but while trying to use some custom themes like Linsta3 (or whichever) I noticed several graphics in the title/menubars/panels did not appear correctly.

Thanks to some help from Artificial Intelligence, I was able to fix the problem by installing/reinstalling a package named: gtk2-engines-pixbuf

```
sudo apt-get install gtk2-engines-pixbuf
```

---

### Post by jonah1980 on 2006-12-11
grey distorted splash screen on boot and shutdown:

[http://www.ubuntuforums.org/showthread.php?t=316137](http://www.ubuntuforums.org/showthread.php?t=316137)

---

### Post by Younes on 2006-12-12
> **nexu56 said:**
> That workaround is incorrect - it affects all players.

[Here is the real workaround.]("http://www.ubuntuforums.org/showthread.php?t=315333")

It works but forces download of the entire file before playing. Not bad for music, but for large video... ](*,)

Incidentally, I think the gedit and the image viewer use this method, which is why they're not affected by the bug like the media players.

---

### Post by Disastorm on 2006-12-13
> **TrendyDark said:**
> I'm not sure if this is a problem in Edgy or just something I ran into, but while trying to use some custom themes like Linsta3 (or whichever) I noticed several graphics in the title/menubars/panels did not appear correctly.

Thanks to some help from Artificial Intelligence, I was able to fix the problem by installing/reinstalling a package named: gtk2-engines-pixbuf

```
sudo apt-get install gtk2-engines-pixbuf
```

thx i have been trying to figure out how to fix this!

---

### Post by psyoptik on 2006-12-20
There is a known bug in edgy regarding kdar and dependencies. The new version of dar 2.3 is incompatible with Kdar 2.x. 

The workaround involves installing two packages from the dapper release into edgy. Check my blog for more info: [http://psyoptik.wordpress.com/2006/12/20/kdar-dependency-fix-for-ubuntu-edgy/](http://psyoptik.wordpress.com/2006/12/20/kdar-dependency-fix-for-ubuntu-edgy/)

---

### Post by Unreadedpost on 2006-12-29
I like to use kde apps like konversation, konqueror, and kate, with gnome, and when I use them the kde apps will blink sometimes in my panel, I'm not sure what it's called, maybe they're active or something, but when I change workspaces(aka desktops) and they're blinking(Referers: [www.unreadedpost.com]("www.unreadedpost.com")) when I do it, they'll be in the worksplace I just switched to. Gnome apps work fine. 

How can I stop this annoying thing? Maybe I can use kcontrol with gnome? Or I would have to switch to kde and use kcontrol?

---

### Post by dragon76 on 2007-01-05
Please add the following workaround for the DPMS bug:

[http://www.ubuntuforums.org/showthread.php?t=323860]("http://www.ubuntuforums.org/showthread.php?t=323860")

I found this to be the best workaround for this problem for me.

Thanks

---

### Post by bristleburger on 2007-01-05
Since upgrading from dapper to edgy I have been having trouble with NFS. Could you add the following to the list of edgy bugs please...

I believe this is a manifestation of bug #62308 originally reported on 25/09/2006.
[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62308](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62308)

Symptoms are as follows:

1. Gnome users settings often revert to default gnome settings when the user logs in to hosts which mount /home over NFS;
2. The following error is often reported when starting evolution on hosts which mount /home over NFS: “Failed to get lock using fcntl(2): Resource temporarily unavailable”;
3. The following error is often reported when starting firefox on hosts which mount /home over NFS: “Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system”;
4. Thumbnails displayed by nautilus (either on the desktop or in file system browser) occasionally revert to basic icons before the preview reappears again a few seconds later. Once again this only occurs on hosts which mount /home over NFS.

Users either logging into the NFS server directly or logging in remotely using the gdm XDMCP chooser experience none of these problems.

Unfortunately my home network is now virtually useless :-(

---

### Post by bristleburger on 2007-01-06
This problem appears to be related to the edgy kernel and can be fixed by reinstalling the the dapper kernel on the NFS server. All NFS clients can continue to run the edgy kernel.

In my case I fixed the problem as follows:
1.Edit /etc/apt/sources.list to add dapper repositories (I added the following)
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports restricted main universe

2.Install linux-image-2.6.15-27-686 and linux-restricted-modules-2.6.15-27-686 using either apt-get or synaptic.

3.Edit /boot/grub/menu.lst to move the 2.6.15-27-686 kernel entry above the 2.6.17-10-generic entry.

4.Reboot.

This seems like a bit of a hack but it appears to fix the problems described in my previous post.

---

### Post by gatewayasteroid on 2007-01-19
[QUOTE=]
**- KDE Screen power saving settings aren't reloaded after reboot**
    * Bug report : [https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/65791](https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/65791)
[https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/66215](https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/66215)
    * Workaround : [http://ubuntuforums.org/showthread.php?p=1819397](http://ubuntuforums.org/showthread.php?p=1819397)
[/QUOTE]

I solved just putting in ~/.kde/Autostart a simple script containing:

[I]sleep 300
xset dpms 0 0 300[/I]

This way, every reboot the DPMS settings are reloaded.

---

### Post by jasutton on 2007-02-02
That should actually take care of it each time you login to KDE :)

---

### Post by Apoorv on 2007-02-23
Where can I get Skype 1.2?

---

### Post by lavinog on 2007-10-21
Why is this still a sticky?

---

### Post by frodon on 2007-10-22
Unstuck, it's a bit old now.

---

