---
title: "Very Frustrated, thinking about dumping Ubuntu"
date: 2007-09-19
forum: General Help
---

### Post by treb0r on 2007-09-19
Hi All,

I posted about this yesterday, but it seems nobody can help me.

To recap, I've been using Ubuntu for a couple of years on my P4 laptop.

I recently decided to start using a new Dell Desktop, so I copied all of my files from the laptop into my new home directory on the desktop.

Then I noticed that sound on the new Dell was broken, but only for my new user account.

Realising that the soundcard in the Desktop is different to the laptop, I thought it would be simple to find the offending dotfile and make the necessary changes. 

How wrong I was. It seems that gconf is a total black art, and it is impossible for me to get the sound working without also dumping my email account settings etc.

Surely there must be a simple way to migrate from one machine to another?

The fact that alsaconf is missing from Ubuntu is another problem.

Please don't tell me to check file ownership and permissions as these are all fine.

If anybody could help me answer these questions I would be very grateful:

What is the best method for migrating data and settings from one machine to another?

How can I get the sound working for my user account on the dell.

Thanks in advance!

---

### Post by firefly2442 on 2007-09-19
Was the sound working before you copied your files over?

---

### Post by jamvegan on 2007-09-19
I'm sorry I don't know for sure how to fix your sound problem.  Those %gconf.xml files are an astonishing morass to try to wade through.  Have you tried fiddling with System->Preferences->Sound?  As for your other question, I just copy files and directories that contain specific user information, or that I have manually edited.  For me, that's .bashrc, .vimrc, .mozilla/ and .mozilla-thunderbird/.

Best of luck!

---

### Post by treb0r on 2007-09-19
> **firefly2442 said:**
> Was the sound working before you copied your files over?

Yes, it was.

As jamvegan says, that whole %gconf.xml morass is a total nightmare.

I can fix my sound by leaving out all the .gconf folders, but then I lose my email account settings.

This is just crazy - I'm at a total loss...

---

### Post by trak87 on 2007-09-19
Be careful not to copy over dot files from one system to another unless absolutely necessary. Systems are different. Sound configuration may be different. I would have copied over all the regular files, but put the dot files in a separate directory and only merged them into the home directory if absolutely necessary, while keeping backups of the originals.

Yes, it's frustrating and would be nice if it were easier, but when you think about it, some configurations only work with a particular system. And systems are different. So it makes sense.

---

### Post by sloggerkhan on 2007-09-19
I try to only move dotfiles for evolution and one or 2 other progs, as well as my  .themes.... If you move some stuff, it might not be compatible with newer versions or different hardware and overide safe/sane defaults.

---

### Post by treb0r on 2007-09-19
> **trak87 said:**
> Be careful not to copy over dot files from one system to another unless absolutely necessary. Systems are different. Sound configuration may be different. I would have copied over all the regular files, but put the dot files in a separate directory and only merged them into the home directory if absolutely necessary, while keeping backups of the originals.

Those dot files store all of my settings that I've taken years to get just right. On most unix systems, you can just move them across, but Ubuntu uses this gconf nightmare. Am I expected to just throw away all my email accounts and other settings just to get the sound working?

Surely the soundcard settings should be set an a per machine basis in /etc anyway.

It just makes no sense

---

### Post by treb0r on 2007-09-19
> **sloggerkhan said:**
> I try to only move dotfiles for evolution and one or 2 other progs, as well as my  .themes.... If you move some stuff, it might not be compatible with newer versions or different hardware and overide safe/sane defaults.

Yes, I realise that, so how do I preserve my email and email accounts, desktop settings, firefox bookmarks, passwords, ssh files etc while not breaking sound on my new machine?

---

### Post by trak87 on 2007-09-19
> **treb0r said:**
> Those dot files store all of my settings that I've taken years to get just right. On most unix systems, you can just move them across, but Ubuntu uses this gconf nightmare. Am I expected to just throw away all my email accounts and other settings just to get the sound working?

Surely the soundcard settings should be set an a per machine basis in /etc anyway.

It just makes no sense

I agree with you. It is a PITA. To me gconf is like the Windows registry: A mess. 

I searched for a gconf export/import tool, but all I found was gconf-editor, which might help. I'm just guessing, but what if you used gconf-editor and deleted the parts that dealt with sound? Perhaps gnome will rebuild those portions when you use a sound app.

---

### Post by trak87 on 2007-09-19
I haven't tried them, but these may be helpful:

gconf editor: [http://hideseek.sourceforge.net/](http://hideseek.sourceforge.net/)

And in the repositories:

sabayon 

gtweakui

---

### Post by GavinZac on 2007-09-19
just as an aside, i guess this is a gnome issue rather than an ubuntu one. If you're going to be doing this regularly, prehaps xubuntu or kubuntu are for you?

i could be wrong though, but i wanted to sound s.m.r.t.

---

### Post by dbott67 on 2007-09-19
I've had similar problems in the past.  I keep my /home directories on a separate partition and after upgrading through Edgy & Feisty, I noticed that I was having some weird sound problems:

1. At the GDM login screen I would sometimes hear the "drum roll" sound.
2. After logging in, I would not hear the **startup.wav** file, although I could hear it if I played it in "Beep" or other music program.
3. In **SYSTEM > PREFERENCES > SOUND > SOUND tab**, the sounds would **not** play.
4. In **SYSTEM > PREFERENCES > SOUND > DEVICES tab**, the **TEST SOUND** worked.
5. Most applications with sound worked (Beep, Totem, Flash video, etc.)
6. No sound in the games "Cube" or "Sauerbraten".
7. All applications worked previously.

After fiddling with the sound settings trying various suggestions in the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") thread, I totally buggered up my sound.  

Oh well, a fresh install of Feisty never hurt anyone and I had my **/home** directory on a separate partition.

After the new install, I still had the 6 symptoms described above.

Thinking that it might be some sort of **.config** file remnant, I created a new user and everything worked properly. A-HA! Comparing the user home directories, I noticed the presence of a **.asoundrc** file and another similarly named file.  After doing some research here about [what the file is for]("http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php") (and it's safe removal), I deleted it, logged out and returned to a system with full working sound.

My suggestion is this:

1. Create a new user account
2. Login using new user account
3. Check to see if sound works properly
4. If it does, then the issue is likely some sort of config file. Look for the [COLOR=Red].asoundrc[/COLOR] file in your original home directory and move it to a backup folder (just in case)
5. Log back in as your original user and test.
6. If it fails to cure the problem, try the Comprehensive Guide above.

-Dave

---

### Post by treb0r on 2007-09-20
HI Dave, thanks for the reply,

I don't seem to have a file named '.asoundrc ' in my home directory.

As far as I can tell, the problem is related to gstreamer, and gstreamer seems to have lots of config files, all controlled by gconf.

I'm considering moving to a new account, but I need to find a way of moving all my settings EXCEPT the sound, so I can keep my passwords, network mounts, tomboy notes, mail etc.

It's unbelievably complex for what should be a trivial task.

I'm wondering if there is some kind of gnome migration helper.

---

### Post by dark_harmonics on 2007-09-20
This does sound like a gnome related issue. if you have the patience you could move one folder at a time (or subfolder) and then log out/in to test. It would be a tedious trial/error process but it should tell you which folder EXACTLY is causing the issue. Then if this folder contains some other important config information test slowly adding its contents in by chunks at a time. 

I know very tedious but nobody seems to know exactly where your problem is coming from here.

---

### Post by treb0r on 2007-09-20
> **dark_harmonics said:**
> This does sound like a gnome related issue. if you have the patience you could move one folder at a time (or subfolder) and then log out/in to test. It would be a tedious trial/error process but it should tell you which folder EXACTLY is causing the issue. Then if this folder contains some other important config information test slowly adding its contents in by chunks at a time. 

I know very tedious but nobody seems to know exactly where your problem is coming from here.

Yes, agreed, it is a Gnome issue, but since I only switched to Gnome because it comes with Ubuntu, I see it as an Ubuntu issue too.

The above sounds like it should work, until you realise that settings for each app are spread across multiple folders, and if one file is missing, the app does not read the settings.

For example, evolution uses the following:

   1. ~/.evolution/
   2. ~/.gconf/apps/evolution/
   3. ~/.gnome2_private/Evolution

Miss any one of these and evolution behaves like it's being run for the first time. Why not just have ALL evolution settings stored in .evolution? No, that would be far too easy.

Add in to this that gconf actually replaces files that are changed or deleted, and you just have a total mess that nobody seems to understand properly. A mess that is home to all my passwords and settings. If I had realised that Gnome / Ubuntu used such a system, I would never have installed it in the first place. Grrr!

---

### Post by Wolki on 2007-09-20
In general, moving dotfiles should not be much of a problem, and I've been doing it lots, If the configuration format has changed, the programs should (and mostly will) update them by themself. The only thing I'm careful about is moving them back and forth between versions, and even that should usually work. 

> **treb0r said:**
> 
For example, evolution uses the following:

   1. ~/.evolution/
   2. ~/.gconf/apps/evolution/
   3. ~/.gnome2_private/Evolution

Miss any one of these and evolution behaves like it's being run for the first time. Why not just have ALL evolution settings stored in .evolution? No, that would be far too easy.

Some are for architectural reasons. Configuration is usually stored in gconf as that offers a variety of lockdown and preconfiguration options to sysadmins, are easily settable even by scripts, support live changes (ie, when the option is changed the program is notified and can adapt to thenew setting immediately etc). It also has some bad sides (especially technically) thats why some people are busy working on an improved version. gconf is not good for storing large amounts of data like your email, caches and similar stuff though, that's why a ~/.evolution is needed. ~/.gnome2_private/Evolution is mostly an arfitfact of the past, iirc it only stores your account information and is setup so that noone but its owner (and of course root) has any access to it. Now you mght wonder "Isn't that exactly what gnome-keyring is for, storing secret stuff so that noone but me can access it? Why have another directory?" And my answer would be that you're right. Problem here is that Evolution is older than gnome-keyring, so it wasn't around when Evo set this up. It was tried some time ago to integrate both programs, but users complained that they now had to unlock their keyring  to acces their email accounts, which was unacceptable to many. I'm not really sure anymore, but I think it also had some bugs. Now that the keyring apparently supports unlocking automatically upon login with 2.20/gutsy , I wouldn't be surprised if we see this integration happening so that ~/.gnome2-private/Evolution will not be needed anymore.
Of course, you'd have to copy the keyring instead, but you'd also keep all your other account data thats managed by gnome-keyring such as wireless keys for network-manager, server accounts for nautilus' "Connect to Server" feature and so on...


Now, enough with my rambling, onward to your sound problem. My first guess was .asoundrc as dbott67 already said since I've already been bitten by it. Apparently that's not the case. So I guess we'll have to gather more information where the problem could lie.
Did you try to change the default sound card? (System -> Preferences -> Audio -> first tab) Play with the settings for a bit. 
Are you using esd? (is a checkbox on the second tab, iirc) If, not try enabling it. If yes, is it actually running? Try "killall esd" followed by "esd" and see whether you hear a sound. 
Start gstreamer-properties and play with the settings and test buttons there a little. 
BTW, which programs are you using to determine whether sound works? Some of them complain what's wrong. 
Take a look at the file ~/.xsession-errors, error/debug output from programs started in X are put there. Do you see anything that could be related to sound?

---

### Post by treb0r on 2007-09-20
> **Wolki said:**
> Now, enough with my rambling, onward to your sound problem. My first guess was .asoundrc as dbott67 already said since I've already been bitten by it. Apparently that's not the case. So I guess we'll have to gather more information where the problem could lie.
Did you try to change the default sound card? (System -> Preferences -> Audio -> first tab) Play with the settings for a bit. 
Are you using esd? (is a checkbox on the second tab, iirc) If, not try enabling it. If yes, is it actually running? Try "killall esd" followed by "esd" and see whether you hear a sound. 
Start gstreamer-properties and play with the settings and test buttons there a little. 
BTW, which programs are you using to determine whether sound works? Some of them complain what's wrong. 
Take a look at the file ~/.xsession-errors, error/debug output from programs started in X are put there. Do you see anything that could be related to sound?

Hi Wolki, thanks for knowledgeable reply.

If I try to change the sound card in System -> Preferences -> Audio -> first tab, it gives the following error when I click 'Test':

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.

If I try to run esd (which is enabled in audio preferences, but not actually running) I get the following error:

ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default

Just to recap, sound is working fine in other user accounts on this box.
Thanks for taking time to help me out...

---

### Post by Wolki on 2007-09-20
> **treb0r said:**
> 
If I try to run esd (which is enabled in audio preferences, but not actually running) I get the following error:

ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default


OK, this is pretty similar to how i remember the .asoundrc error. For some reason your system is trying to access the wrong soundcard (the one in your old computer). I have no clue why this should be set in gconf...

Let's see whether we can get alsa to access the real soundcard. Do this: "asoundconf list". You should get one or more sound card names. Choose the correct one, then do "asoundconf set-default-card <correct sound card name>" Then see if you can start esd now. (you might have to log out, i'm not sure)

If it didn't work tell me and i'll think more about it.

---

### Post by treb0r on 2007-09-20
Wolki,

rob@loo:~$ asoundconf list
Names of available sound cards:
Intel

I've set the default card to 'Intel'

Now esd gives the following error:

ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'Intel'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default

Thanks again..

---

### Post by Wolki on 2007-09-20
Very weird. For some reason alsa seems messed up. Can you try doing
"sudo /etc/init.d/alsa-utils reset" and repeat the steps from the last post?

[edit] searching around for a bit, there seems to be a known bug with intel soundcards Can you try the following:
```
kill $(lsof -t /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/*) ; sudo modprobe -r $(lsmod |grep ^snd |awk '{print $1}') && sudo modprobe snd-hda-codec && sudo modprobe snd-hda-intel model=auto
```

---

### Post by treb0r on 2007-09-21
Hi Wolki,

I get the following output:

FATAL: Module snd_hda_codec not found.


Thanks..

---

### Post by mikewhatever on 2007-09-21
This thread reaffirms my decision to never use an email client.Have you checked if evolution has some kind of settings transfer utility?

---

### Post by treb0r on 2007-09-21
> **mikewhatever said:**
> This thread reaffirms my decision to never use an email client.Have you checked if evolution has some kind of settings transfer utility?

Nope, but I did find this:

[http://ubuntu.wordpress.com/2005/12/03/how-to-backup-evolution/](http://ubuntu.wordpress.com/2005/12/03/how-to-backup-evolution/)

Which is good enough. Still can't get the damn sound working. I'm going to wait till Gutsy is released, then reinstall from scratch. Joy of joys.

---

### Post by chuckyp on 2007-09-21
There is no need to wade through all of the XML files for gconf.  Open a terminal and run gconf-editor.  Or hit Alt+F2 and type in gconf-editor.  This will bring up a nice GUI similar to windows registry edit but easier to understand.  I would just look through all your settings for sound in there. Possibly compare them to that of another user since that is working for you.

To get the other users gconf up you could 
```

sudo su - otheruser

```
in a terminal.  Then run gconf-editor as that user.

You should be able to compare the differences pretty easily then.

---

### Post by treb0r on 2007-09-21
> **chuckyp said:**
> There is no need to wade through all of the XML files for gconf.  Open a terminal and run gconf-editor.  Or hit Alt+F2 and type in gconf-editor.  This will bring up a nice GUI similar to windows registry edit but easier to understand.  I would just look through all your settings for sound in there. Possibly compare them to that of another user since that is working for you.

To get the other users gconf up you could 
```

sudo su - otheruser

```
in a terminal.  Then run gconf-editor as that user.

You should be able to compare the differences pretty easily then.

I've already had a look at this - I can't make any sense of what needs to change - again, there are multiple entries for gstreamer, some of which don't appear to be editable..

---

### Post by Wolki on 2007-09-21
> **treb0r said:**
> I've already had a look at this - I can't make any sense of what needs to change - again, there are multiple entries for gstreamer, some of which don't appear to be editable..

gstreamer settings shouldn't affect your sound overall, especially not such that alsa can't find your sound card anymore.

Are you sure that it's gconf and not some other file creating the problem?

If yes, one thing you could do is post the structure of your .gconf directory so we can see which sections have changes. (da a "find ." in ~/.gconf" and post  the output here, it's probably rather large so it might be best to put it in code tags)

---

### Post by treb0r on 2007-09-21
I've had a geek friend over to take a look and after two hours, he admitted defeat. 

I'm going to reinstall, bin the dotfiles and just move the evolution stuff over.

Thanks a lot for you efforts - I'm going to stay with Ubuntu for the time being, just by virtue of the helpful community, although I still think the whole gconf thing sucks big time.

---

### Post by teledyn on 2007-09-25
I have been using Ubuntu Feisty for two weeks now, complete with sound, on a Dell Inspiron 1521 laptop that uses the HDA audio.  It was working perfectly, playing sound files through aplay, mpg321 and RhythmBox, no problems.

Until this morning.

Occasionally I find that if I play a youtube video on Firefox, the sound is locked into Firefox and I must exit the browser to get the sounds to play.  I exit the browser, still no sound.  I shut down all apps, no sound, I logout and login, no sound, I do a hard reboot, and no sound!!!!

except, of course, for my screams ...

I now have all the symptoms reported here except that I do not see anything listed by 
$ asoundconf list

and modprobe evokes the following:

Sep 25 10:11:31 uhuru kernel: [  811.040000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Sep 25 10:11:32 uhuru kernel: [  812.364000] hda_intel: azx_get_response timeout, switching to polling mode...
garym@uhuru:~$ Sep 25 10:11:33 uhuru kernel: [  813.372000] hda_codec: No auto-config is available, default to model=ref

lspci says the device is unknown and "access denied"!

00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
        Subsystem: Dell Unknown device 01fc
        Flags: slow devsel, IRQ 16
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

now ... here is a possible new clue: the last thing to be added to this laptop was the drivers for the modem ...

$ more /etc/modprobe.d/hsf
alias /dev/ttySHSF[0-9]* /dev/ttySHSF
alias /dev/modem /dev/ttySHSF
alias char-major-240 /dev/ttySHSF
alias char-major-240-* /dev/ttySHSF
options hsfserial serialmajor=240
alias char-major-242 hsfosspec
alias char-major-242-* hsfosspec
alias /dev/hsfdiag hsfosspec
alias /dev/hsfdiag* /dev/hsfdiag
alias char-major-243 /dev/hsfdiag
alias char-major-243-* /dev/hsfdiag
options hsfosspec dcpmajor=242 diagmajor=243
install /dev/ttySHSF /sbin/modprobe hsfpcibasic2; /sbin/modprobe hsfmc97ich; /sb
in/modprobe hsfmc97via; /sbin/modprobe hsfmc97ali; /sbin/modprobe hsfmc97ati; /s
bin/modprobe hsfmc97sis; [ -e /lib/modules/`uname -r`/extra/hsfusbcd2.ko ] && /s
bin/modprobe hsfusbcd2; /sbin/modprobe snd_hda_intel; /bin/true
alias symbol:cnxthwhda_probe hsfhda
alias symbol:cnxthwhda_resume hsfhda
alias symbol:cnxthwhda_suspend hsfhda

anything in there that might be the cause? I'm totally stymied, grabbing at straws.

Everything seemed to be going so well, but now it looks like I lose yet another day's work spent bashing my head against drivers. It *was* working just fine last night, nothing was done between then and now (the modem driver was installed several days ago) no reboots, no log-outs, maybe a screensaver and that's it.  

very frustrating, and while _I_ know the *true* cause of everyone's frustration is not Ubuntu or Linux but the idiot hardware manufacturers who shove their proprietary driver code firmly up where the moon don't shine, it is still frustrating, and I just know work is going to be on my case again for putting Linux on this machine :( ...

---

### Post by teledyn on 2007-09-25
[Ubuntu Bug 128085]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/128085") details these effects and the discussion leans towards obtaining [updated ALSA drivers from the snapshots]("ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/") -- if this is a fix, it should be folded in as an update asap.

There was one other change with my machine overnight: I installed the latest bug-fix (security fix) kernel package, and that *may* have replaced my working snd-hda-intel driver with a broken one, which perhaps for whatever reason we reloaded after the update.

---

