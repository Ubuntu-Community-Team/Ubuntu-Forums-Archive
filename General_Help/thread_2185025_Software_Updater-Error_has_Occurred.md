---
title: "Software Updater-Error has Occurred"
date: 2013-10-31
forum: General Help
---

### Post by smith-chad12 on 2013-10-31
First off I will say I am pretty new to Ubuntu as I have only been running it for about 3 weeks now.  For those three weeks it was been running flawless though.

Anyway, I am running Ubuntu 13.10 and yesterday I received a notification for some updates.  I had the time so I went ahead and downloaded and installed them.  While it was installing some updates an error message occurred saying that the package was broken.  I tried it again and nothing.  I tried to click repair and I get the same error notification.

Now in the menu bar I have a Red Error Notification Icon telling me to run the package manager or apt-get from the terminal to see what is wrong.  I tried doing the terminal and it suggest to do 
```
apt-get install -f
```  It asks if I want to continue this operation and I say yes.  It acts like it is installing the package when at the end it gives another error message.   Here is what terminal outputs to me after saying yes to continue

```
Get:1 http://ppa.launchpad.net/jacob/media/ubuntu/ saucy/main librhythmbox-core8 amd64 3.0.1-1ubuntu2~ppa0 [819 kB]Fetched 819 kB in 2s (277 kB/s)             
(Reading database ... 178391 files and directories currently installed.)
Unpacking librhythmbox-core8 (from .../librhythmbox-core8_3.0.1-1ubuntu2~ppa0_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/librhythmbox-core8_3.0.1-1ubuntu2~ppa0_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/librhythmbox-core.so.8.0.0', which is also in package librhythmbox-core7 3.0.1-0~13.10~ppa1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/librhythmbox-core8_3.0.1-1ubuntu2~ppa0_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

Anything I try with apt-get doesn't seem to work as it always goes back to try to install those packages and it asks me too try apt-get install -f again.  Now even when I open up the Software Center it gives me an error message saying new software can't be installed as their is a problem with the software currently installed.  It asks me if I want to repair it?  I go ahead and say yes and it again pops up an error message saying the package operation has failed.

When I try to run Software Updater it checks for updates as it should and it finds those updates It lists updates under "Ubuntu Base."  I go and ahead and click install now and it again gives me a Package Operation error. 

So now I'm basically stuck.  I can't install any new software at all it seems anything I do with apt-get wants to to do install -f again.

Anyone have any suggestions?  It seems the files are already downloaded just need to be installed.  Anyway I can get the files to be re-downloaded if maybe somehow they became corrupt?  If you need any more information then just let me know and I'll tell you what you need to know.

PS: Sorry if this is the wrong section for this question.  I wasn't sure what this would fall under.

---

### Post by ian-weisser on 2013-10-31
> **smith-chad12 said:**
> 
Unpacking [COLOR=#ff0000]librhythmbox-core8[/COLOR] (from .../librhythmbox-core8_3.0.1-1ubuntu2~ppa0_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/librhythmbox-core8_3.0.1-1ubuntu2~ppa0_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/librhythmbox-core.so.8.0.0', which is also in package [COLOR=#ff0000]librhythmbox-core7[/COLOR] 3.0.1-0~13.10~ppa1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)


You broke your package system with one or more PPAs.
That's a risk of PPAs, and one reason PPAs are not supported.

How to fix it: 

1) Open your Software Sources control panel
It's in Software Center --> Edit --> Software Sources
Uncheck the PPA that provides rhythmbox, but breaks your system: [http://ppa.launchpad.net/jacob/media/ubuntu/](http://ppa.launchpad.net/jacob/media/ubuntu/)
(By the way, Rhythmbox in the Ubuntu repositories *is* fully supported, and won't break your system)

2)  Open a Terminal
Delete the problem package from your local cache with the command **sudo apt-get clean librhythmbox-core8**

See if your package manager works again: **sudo apt-get update && sudo apt-get upgrade**

If it does not work, post the results here.

You may need to completely uninstall the rest of the PPA packages, an error message will tell us.

---

### Post by smith-chad12 on 2013-10-31
Thanks a lot for the quick reply
I did as you said and then ran the apt-get update and upgrade and everything seemed to be going well with it then at the very end I saw it spit out close to the same thing that it had been spitting out before:

```
Building dependency tree       Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gir1.2-rb-3.0 : Depends: librhythmbox-core8 (>= 3.0.1) but it is not installable
 rhythmbox : Depends: librhythmbox-core8 (= 3.0.1-1ubuntu2~ppa0) but it is not installable
 rhythmbox-plugin-cdrecorder : Depends: librhythmbox-core8 (>= 3.0) but it is not installable
 rhythmbox-plugins : Depends: librhythmbox-core8 (= 3.0.1-1ubuntu2~ppa0) but it is not installable
E: Unmet dependencies. Try using -f

```

Thanks again for the help.  Greatly appreciate it.

---

### Post by ian-weisser on 2013-10-31
Well, that's the error message we were waiting to see...
It's progress.

Remove the all packages that depend upon the removed librhythmbox-core8
Also clean them from your local cache.
Finally, test the package manager to see if any error messages remain.

Er, this will of course completely uninstall rhythmbox. After your package manager is working again you can easily reinstall...but not from that PPA; it will promptly break your system again.
```
sudo dpkg --remove rhythmbox
sudo dpkg --remove gir1.2-rb-3.0
sudo dpkg --remove rhythmbox-plugin-cdrecorder
sudo dpkg --remove rhythmbox-plugins
sudo apt-get autoremove
sudo apt-get clean gir1.2-rb-3.0
sudo apt-get clean rhythmbox-plugin-cdrecorder
sudo apt-get clean rhythmbox-plugins
sudo apt-get update && sudo apt-get upgrade

```

---

### Post by smith-chad12 on 2013-10-31
hmmm, I must not be removing a correct ppa or I missed one?

it seems to remove everything just fine except for rhythmbox itself.  When doing rhythmbox-plugins-cdrecorder and rhythmbox-plugins it removes just fine but for rhythmbox itself it gives the error:

```
dpkg: dependency problems prevent removal of rhythmbox: rhythmbox-ubuntuone depends on rhythmbox (>= 2.95.5).


dpkg: error processing rhythmbox (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 rhythmbox



```

So I still can't do the update without it providing the same error as before.  Thing is though from what I can see from the Software Sources it seems I should only have default software sources.  So I am a bit confused and lost now?

I'm sorry for seeming like such a noob with this.  I know technology pretty well and am an Undergraduate Computer Science Major I'm just new to Linux/Ubuntu so I'm trying to work my way around it and figure out how it works and figure out the terminal still...

---

### Post by ian-weisser on 2013-11-01
Another package depends upon rhythmbox, that's all.
Since the package probably didn't come from the PPA, we need only uninstall it - we don't need to clean it from the local package cache.
We do still need to remove the PPA version of rhythmbox from the cache.
```
sudo dpkg --remove rhythmbox-ubuntuone
sudo dpkg --remove rhythmbox
sudo apt-get clean rhythmbox
sudo apt-get autoremove
sudo apt-get update && sudo apt-get upgrade
```

Let us know if any other new problems crop up...

---

### Post by smith-chad12 on 2013-11-02
Very sorry for the late reply back.  I got busy with work yesterday and I haven't been around my computer today until now.

Again thanks for the help and your continue support to help me out.  Sadly I am still running into issues.  The commands work great until I get to autoremove.  When I do that one I receive pretty much the same output I have been getting.  Here is my output from where I first try autoremove.

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 rhythmbox-mozilla : Depends: rhythmbox (= 3.0.1-1ubuntu2~ppa0) but it is not installed
 rhythmbox-plugin-magnatune : Depends: rhythmbox (= 3.0.1-1ubuntu2~ppa0) but it is not installed
 rhythmbox-plugin-zeitgeist : Depends: rhythmbox (>= 3.0) but it is not installed
                              Depends: rhythmbox (< 3.1) but it is not installed
E: Unmet dependencies. Try using -f.



```

Which of course cause the same output/errors if I try to update it.

Even though I know this isn't really a "fix" for this since I am sure this issue will/could more than likely be fixed soon if you can continue to help me, but since I have only ran Ubuntu for around 3 weeks I really don't have anything important installed/saved on this partition yet, and anything I've saved is actually on my external drive.  So I could do a reinstall to start fresh if needed...

Again I GREALY appreciate anymore help.  I really don't mean to be pain.  I just seem to be confused on what ppa I did that screwed it up so bad.  I'm sure I made a dumb mistake somewhere.  :-k

---

### Post by ian-weisser on 2013-11-03
This is a minor, solvable problem. I don't think it is worth a reinstall.
Any PPA has the risk of causing this kind of problem. You can use PPAs all you like, but you should understand how to remove them manually.

Do you see the pattern of removing dependencies here?
Let's remove those three packages, and remove them from the local cache:
```
sudo dpkg --remove rhythmbox-mozilla
sudo dpkg --remove rhythmbox-plugin-magnatune
sudo dpkg --remove rhythmbox-plugin-zeitgeist
sudo apt-get clean rhythmbox-mozilla
sudo apt-get clean rhythmbox-plugin-magnatune
sudo apt-get clean rhythmbox-plugin-zeitgeist
sudo apt-get autoremove
sudo apt-get update && sudo apt-get upgrade
```

We are making progress!
First, you didn't understand the message at all.
Then you removed the offending packages.
The you removed the dependencies.
Now you are removing packages that depend upon rhythmbox (reverse dependencies).
Depending on the resulting error messages, there are one or two more iterations...and then it's fixed, good as new!

The next part seems scary, but **WON'T** damage your system, and is a normal step in fixing your kind of problem. A package called ubuntu-desktop depends upon those rhythmbox plugins, and we should start seeing ubuntu-desktop errors next. **IT'S OKAY**. Ubuntu-desktop is actually a package that can be safely removed - it **WON'T** really remove your whole desktop, or lose any of your data. We can reinstall ubuntu-desktop later when we finish fixing the problem.

---

### Post by smith-chad12 on 2013-11-03
Well that step seemed to do the trick actually!  I received no errors and the update and upgrade seemed run flawless.  No errors were reported.  Did a quick reboot, the error icon I had is no longer displayed and now I can go into the Software Center without getting an error message about a broken package.

Would their be anything else I would need to do?  I would think a reinstall of RhythmBox would be in order.  Would there be anything else?  Again, greatly appreciate all the help you have provided!

---

### Post by ian-weisser on 2013-11-03
Happy to see it working!

If you plan to use Rhythmbox, then indeed you should reinstall it using Software Center or the terminal (**sudo apt-get install rhythmbox**)
Either method should install the Ubuntu Repository version of Rhythmbox, not the PPA version that caused problems. You disabled that PPA.

If you don't plan to use rhythmbox, then you are not required to install it.

There is nothing else you need to do to "clean up" or "finish". You already did it.

Don't forget to use the forum's Thread Tools (at the top of the page) to mark the thread as SOLVED.

---

