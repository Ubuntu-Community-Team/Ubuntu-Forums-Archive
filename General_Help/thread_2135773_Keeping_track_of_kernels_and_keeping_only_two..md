---
title: "Keeping track of kernels and keeping only two."
date: 2013-04-15
forum: General Help
---

### Post by Cavsfan on 2013-04-15
Not sure where I got this but, I think it is a handy way to keep track of your kernels.
When I get a new kernel install I copy it from the terminal and past it to a gedit file. I name the file **kernel cmds for Raring** (or whatever version I am on). So I can find it easily in

When I enter **sudo apt-get update && sudo apt-get upgrade** and see files that will be installed and also see this:

```
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
```

After I install the updates I enter **sudo apt-get dist-upgrade** to install the kernel but before I press "Y" to install it I first copy the file names (in red) and paste them to the gedit file.

```
The following NEW packages will be installed:
  [COLOR=#ff0000]linux-headers-3.8.0-18 linux-headers-3.8.0-18-generic linux-image-3.8.0-18-generic linux-image-extra-3.8.0-18-generic[/COLOR]
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 56.4 MB of archives.
After this operation, 235 MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

While pasting the file names into the gedit text file I put "sudo apt-get purge" before each line for later use.
So then I delete any I have besides the last 2 kernels.

Here is what my text file looks like for Raring:
```
sudo apt-get purge linux-headers-3.8.0-9 linux-headers-3.8.0-9-generic linux-image-3.8.0-9-generic linux-image-extra-3.8.0-9-generic        - deleted.

sudo apt-get purge linux-headers-3.8.0-10 linux-headers-3.8.0-10-generic linux-image-3.8.0-10-generic linux-image-extra-3.8.0-10-generic    - deleted.

sudo apt-get purge linux-headers-3.8.0-11 linux-headers-3.8.0-11-generic linux-image-3.8.0-11-generic linux-image-extra-3.8.0-11-generic    - deleted.

sudo apt-get purge linux-headers-3.8.0-12 linux-headers-3.8.0-12-generic linux-image-3.8.0-12-generic linux-image-extra-3.8.0-12-generic    - deleted.

sudo apt-get purge linux-headers-3.8.0-13 linux-headers-3.8.0-13-generic linux-image-3.8.0-13-generic linux-image-extra-3.8.0-13-generic    - deleted.

sudo apt-get purge linux-headers-3.8.0-14 linux-headers-3.8.0-14-generic linux-image-3.8.0-14-generic linux-image-extra-3.8.0-14-generic    - deleted.

sudo apt-get purge linux-headers-3.8.0-15 linux-headers-3.8.0-15-generic linux-image-3.8.0-15-generic linux-image-extra-3.8.0-15-generic    - deleted.

sudo apt-get purge linux-headers-3.8.0-16 linux-headers-3.8.0-16-generic linux-image-3.8.0-16-generic linux-image-extra-3.8.0-16-generic

sudo apt-get purge linux-headers-3.8.0-17 linux-headers-3.8.0-17-generic linux-image-3.8.0-17-generic linux-image-extra-3.8.0-17-generic

sudo apt-get purge linux-headers-3.8.0-18 linux-headers-3.8.0-18-generic linux-image-3.8.0-18-generic linux-image-extra-3.8.0-18-generic

linux-image-generic linux-generic linux-headers-generic
```

(The last 2 files are just part of the kernel but, I don't touch them unless I have deleted the last kernel and need to reinstall it which _**I do not recommend**_)

So, I have just installed the 3.8.0-18 kernel and will reboot. Then I will come back and delete the 3.8.0-16 kernel with the above line and copy and paste the **- deleted** part and save it.

Then to make it even simpler I have these aliases that do the above commands called **ud** and **ud2**. Someone in this forum told me how to do this:

**gksu gedit ~/.bashrc**

Then copy the blue lines after the others (the others are around line 87).

```
# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

[COLOR=#0000ff]# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias ud2='sudo apt-get dist-upgrade'[/COLOR]
```



Then all you have to do is enter **ud** and your password in terminal to get your updates and if anything is held back enter **ud2**.
Doing it this way you never have to worry about partial upgrades because if it is not ready to install it will still say **The following packages have been kept back:**

Here is what my text file looks like for Quantal:
```
sudo apt-get purge linux-headers-3.5.0-25 linux-headers-3.5.0-25-generic linux-image-3.5.0-25-generic linux-image-extra-3.5.0-25-generic    - deleted.

sudo apt-get purge linux-headers-3.5.0-26 linux-headers-3.5.0-26-generic linux-image-3.5.0-26-generic linux-image-extra-3.5.0-26-generic

sudo apt-get purge linux-headers-3.5.0-27 linux-headers-3.5.0-27-generic linux-image-3.5.0-27-generic linux-image-extra-3.5.0-27-generic
```

Here is what my text file looks like for Precise (notice there are only 3 kernel files for Precise):
```
sudo apt-get purge linux-headers-3.2.0-37 linux-headers-3.2.0-37-generic linux-image-3.2.0-37-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-38 linux-headers-3.2.0-38-generic linux-image-3.2.0-38-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-39 linux-headers-3.2.0-39-generic linux-image-3.2.0-39-generic

sudo apt-get purge linux-headers-3.2.0-40 linux-headers-3.2.0-40-generic linux-image-3.2.0-40-generic
```

Here is my Mint 14 Nadia kernel file which is identical to the Quantal one, which Mint 14 is based on:
```
sudo apt-get purge linux-headers-3.5.0-26 linux-headers-3.5.0-26-generic linux-image-3.5.0-26-generic linux-image-extra-3.5.0-26-generic

sudo apt-get purge linux-headers-3.5.0-27 linux-headers-3.5.0-27-generic linux-image-3.5.0-27-generic linux-image-extra-3.5.0-27-generic

```
PS: Thank you forum auto save feature!!! :D I clicked the top close button to close the text file and since my Raring is finicky about the buttons when maximized, it closed Firefox. :(
I thought I lost everything but, then I remembered how it auto saved the data periodically.
I found "start a new thread" in my history and clicked on it but it was empty. :( then I seen at the bottom "restore autosaved data" or something similar and viola it all came back. :D

---

### Post by brainwash on 2013-04-15
Starting with Ubuntu 13.04 (Raring), there is actually no need for this, because apt-get marks older kernel packages as "for autoremoval" and only keeps the two latest ones. Simply run this command once in a while:
```
sudo apt-get autoremove --purge
```

---

### Post by Bucky Ball on 2013-04-15
I use Grub Customizer myself to keep the menu list at boot in order. You can rename the kernels, reorder them and remove them from the list. 

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by schragge on 2013-04-15
I usually do it with a shell script like this:
```

#!/bin/sh
cur=$(uname -r)
prev=$(readlink -f /vmlinuz.old) && prev=${prev#*-} || prev=@
keepkernels="^linux-(headers|image|image-extra)-($cur|$prev)"
allkernels='^linux-(headers|image|image-extra)-[0-9]'
exec sudo apt-get --only-upgrade purge "$allkernels" "$keepkernels"+

```
But solution suggested by **brainwash** above is a lot simpler.

---

### Post by Cavsfan on 2013-04-15
Thanks for the posts but, I was just trying to give people a simple way to manage their kernels. 

You can't get much simpler than this and I trust those commands more than I trust anything else.
I am purging 4 files by name and this way I know exactly what to expect: that those 4 files will be purged.

I prefer to keep it simple so I know exactly what is going to happen, which is what I posted above.

I also stay away from Grub Customizer because I already have a way to customize my Grub menu (the [COLOR=green]green[/COLOR] link in my signature).

---

### Post by Cavsfan on 2013-04-22
Anyone else find this an easy way to keep track of your kernels? Since they say you should always keep two kernels, 
once I found the file names I made the text file and have been doing it this way for about 4 years. I found it easiest to copy the file names from the terminal just before intstallation.

---

### Post by tomdkat on 2013-04-27
> **brainwash said:**
> Starting with Ubuntu 13.04 (Raring), there is actually no need for this, because apt-get marks older kernel packages as "for autoremoval" and only keeps the two latest ones. Simply run this command once in a while:
```
sudo apt-get autoremove --purge
```So, I upgraded to Ubuntu 13.04 today and noticed 6 2.6.x kernels were left behind.  I ran the command you mention and the 2.6.x kernels were not removed.

Am I missing something here or must something else be done to clean up the old 2.6.x kernels?

Thanks!

Peace...

---

### Post by ibjsb4 on 2013-04-27
I just use [synaptic package manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels+synaptic+package+manager&sa=Search&cof=FORID:9")

```
sudo apt-get install synaptic
```
[URL="http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels+synaptic+package+manager&sa=Search&cof=FORID:9"]
[/URL]

---

### Post by Cavsfan on 2013-04-28
> **tomdkat said:**
> So, I upgraded to Ubuntu 13.04 today and noticed 6 2.6.x kernels were left behind.  I ran the command you mention and the 2.6.x kernels were not removed.

Am I missing something here or must something else be done to clean up the old 2.6.x kernels?

Thanks!

Peace...

If you are refering to 
```
sudo apt-get autoremove --purge
``` 
I cannot help you. That is not what this thread is about.

> **ibjsb4 said:**
> I just use synaptic package manager.

```
sudo apt-get install synaptic
```
[URL="http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels+synaptic+package+manager&sa=Search&cof=FORID:9"]
[/URL]

Sure you can use SPM to remove them after finding them which can sometimes take a bit of looking.
Whether you use SPM or the command:

```
sudo apt-get purge linux-headers-blah.blah-blah linux-headers-blah.blah-blah-generic linux-image-blah.blah-blah-generic linux-image-extra-blah.blah-blah-generic
```
will pretty much accomplish the same thing as long as you do not delete the wrong files or not all of them using SPM.

As I stated in post #1 (which this thread *is* about):
When updating kernels I copied the names of the components of the kernel and pasted them into a text (gedit) file thus keeping track of the kernels as they are installed.

```
The following NEW packages will be installed:
  [COLOR=#FF0000]linux-headers-3.8.0-18 linux-headers-3.8.0-18-generic linux-image-3.8.0-18-generic linux-image-extra-3.8.0-18-generic[/COLOR]
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 56.4 MB of archives.
After this operation, 235 MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

I am merely *suggesting* my method of copying these kernel file names from the commands above and pasting them into a text file to log them if you will.
Then subsequently deleting the 3rd one back and leaving 2 kernels.
You can do it however you see fit. ;)

---

### Post by schragge on 2013-04-28
> **tomdkat said:**
> So, I upgraded to Ubuntu 13.04 today and noticed 6 2.6.x kernels were left behind.  I ran the command you mention and the 2.6.x kernels were not removed.I'm not sure what **brainwash** was referring to (I don't use Ubuntu myself). But obviously for that to work, kernel packages should be marked as auto-installed, and some installed packages should depend only on the last two of them. AFAICS, the dependency tree in raring looks like
```

linux -> linux-generic -> linux-headers-generic -> linux-headers-3.8.0-19-generic
              +-> linux-image-generic -> linux-image-3.8.0-19-generic
                       +-> linux-image-extra-3.8.0-19-generic
                       +-> linux-firmware

```
If all those packages but *linux* are marked as auto-installed then upgrading *linux* could clear previously installed versions of *linux-image-** and *linux-image-extra-** for autoremoval. But I still don't see how it could keep _two_ kernels as [linux-image-generic](http://packages.ubuntu.com/raring/linux-image-generic) only depends on one.
 
To manually mark packages as auto-installed, run [apt-mark]("http://manpages.ubuntu.com/manpages/raring/en/man8/apt-mark.8.html")
```

sudo apt-mark manual linux
sudo apt-mark auto ^linux-

```

---

### Post by Cavsfan on 2013-04-29
> **schragge said:**
> I'm not sure what **brainwash** was referring to ([COLOR=#ff0000]I don't use Ubuntu myself[/COLOR]).



 schragge, it doesn't matter what brainwash was referring to, you both veered off topic and both of your comments are irrelevant to this thread.

---

### Post by ibjsb4 on 2013-04-29
> **Cavsfan said:**
> Sure you can use SPM to remove them after finding them which can sometimes take a bit of looking.

Sorry, but compared to post #1, this looks like a breeze.

[ATTACH=CONFIG]241952[/ATTACH]

---

### Post by Cavsfan on 2013-04-30
> **ibjsb4 said:**
> Sorry, but compared to post #1, this looks like a breeze.

[ATTACH=CONFIG]241952[/ATTACH]

Once again, :roll: I started this thread to help people keep track of their kernels copying and pasting the file names _*as they are installed*_ using a text editor and CLI commands.
I do not see how much easier it can get than that. instead of making alternate suggestions why don't you go start your own thread on how easy it is to use Synapic Package Manager 
to remove the kernels files. That should be interesting. :p

---

### Post by ibjsb4 on 2013-04-30
snip :)

---

### Post by QIII on 2013-04-30
Let's cut the sniping.  OK?

---

### Post by Cavsfan on 2013-04-30
> **QIII said:**
> Let's cut the sniping.  OK?

Thank you QIII! :)

---

### Post by ibjsb4 on 2013-04-30
> **ibjsb4 said:**
> snip :)

I did that and your welcome.

---

### Post by QIII on 2013-04-30
That would be "snipping".

;)

---

### Post by CharlesA on 2013-04-30
How is the commands in the OP that much different from this (really nasty looking) one-liner?

```
apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | sort -t- -k3 | head -n -3)
```

[http://ubuntuforums.org/showpost.php?p=12444039&postcount=31](http://ubuntuforums.org/showpost.php?p=12444039&postcount=31)

---

### Post by schragge on 2013-05-01
The sed expression above won't work in all circumstances, especially if you have packages from different architectures co-installed:
```

[COLOR=green]$[/COLOR] dpkg -l linux-\*|awk '/^ii/,$0=$2'
[COLOR=green]linux-base
linux-doc
linux-doc-3.2
linux-image-3.2.0-4-amd64
linux-image-amd64
linux-libc-dev:amd64
linux-libc-dev:i386[/COLOR]

```
or are running [release candidate kernels]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.9-rc8-raring/") or kernels from some other PPAs / 3rd party repositories.

But it could be rewritten like this
```
sudo apt-get purge $(ls -rv /lib/modules | sed -n '3,$s/^/^linux-.\\*-/p')
```
or, if you prefer awk
```
sudo apt-get purge $(ls -rv /lib/modules | awk 'NR>2,sub(/^/,"^linux-.\\*-")')
```
If the kernel you are currently running is not the latest installed version then you could add to this a precaution not to purge the running kernel:
```
sudo apt-get purge $(ls -I`uname -r` -rv /lib/modules | sed '1d;s/^/^linux-.\\*-/')
```

---

### Post by Cavsfan on 2013-05-01
> **CharlesA said:**
> How is the commands in the OP that much different from this (really nasty looking) one-liner?

```
apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | sort -t- -k3 | head -n -3)
```

[http://ubuntuforums.org/showpost.php?p=12444039&postcount=31](http://ubuntuforums.org/showpost.php?p=12444039&postcount=31)

> **schragge said:**
> The sed expression above won't work in all circumstances, especially if you have packages from different architectures co-installed:
```

[COLOR=green]$[/COLOR] dpkg -l linux-\*|awk '/^ii/,$0=$2'
[COLOR=green]linux-base
linux-doc
linux-doc-3.2
linux-image-3.2.0-4-amd64
linux-image-amd64
linux-libc-dev:amd64
linux-libc-dev:i386[/COLOR]

```
or are running [release candidate kernels]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.9-rc8-raring/") or kernels from some other PPAs / 3rd party repositories.

But it could be rewritten like this
```
sudo apt-get purge $(ls -rv /lib/modules | sed -n '3,$s/^/^linux-.\\*-/p')
```
or, if you prefer awk
```
sudo apt-get purge $(ls -rv /lib/modules | awk 'NR>2,sub(/^/,"^linux-.\\*-")')
```
If the kernel you are currently running is not the latest installed version then you could add to this a precaution not to purge the running kernel:
```
sudo apt-get purge $(ls -I`uname -r` -rv /lib/modules | sed '1d;s/^/^linux-.\\*-/')
```

LOL Guys!
I would never take a chance on a script to do something like this, I prefer keeping it REAL simple: like this text file for Raring:
```

sudo apt-get purge linux-headers-3.8.0-9 linux-headers-3.8.0-9-generic linux-image-3.8.0-9-generic linux-image-extra-3.8.0-9-generic        - deleted.  
sudo apt-get purge linux-headers-3.8.0-10 linux-headers-3.8.0-10-generic linux-image-3.8.0-10-generic linux-image-extra-3.8.0-10-generic    - deleted.  
sudo apt-get purge linux-headers-3.8.0-11 linux-headers-3.8.0-11-generic linux-image-3.8.0-11-generic linux-image-extra-3.8.0-11-generic    - deleted.  
sudo apt-get purge linux-headers-3.8.0-12 linux-headers-3.8.0-12-generic linux-image-3.8.0-12-generic linux-image-extra-3.8.0-12-generic    - deleted.  
sudo apt-get purge linux-headers-3.8.0-13 linux-headers-3.8.0-13-generic linux-image-3.8.0-13-generic linux-image-extra-3.8.0-13-generic    - deleted.  
sudo apt-get purge linux-headers-3.8.0-14 linux-headers-3.8.0-14-generic linux-image-3.8.0-14-generic linux-image-extra-3.8.0-14-generic    - deleted.  
sudo apt-get purge linux-headers-3.8.0-15 linux-headers-3.8.0-15-generic linux-image-3.8.0-15-generic linux-image-extra-3.8.0-15-generic    - deleted.  
sudo apt-get purge linux-headers-3.8.0-16 linux-headers-3.8.0-16-generic linux-image-3.8.0-16-generic linux-image-extra-3.8.0-16-generic    - deleted.  
sudo apt-get purge linux-headers-3.8.0-17 linux-headers-3.8.0-17-generic linux-image-3.8.0-17-generic linux-image-extra-3.8.0-17-generic  
sudo apt-get purge linux-headers-3.8.0-18 linux-headers-3.8.0-18-generic linux-image-3.8.0-18-generic linux-image-extra-3.8.0-18-generic 
```

Real simple. :-k

Those kernels are starting way back in the development cycle of Raring. I think after a clean install I just have the last one installed. I just used the old list for example.

---

### Post by CharlesA on 2013-05-01
I thought it wasn't a good idea to do stuff like that with ls?
[http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

Maybe I'm just missing the point. :)

---

### Post by Cavsfan on 2013-05-01
> **CharlesA said:**
> I thought it wasn't a good idea to do stuff like that with ls?
[http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

Maybe I'm just missing the point. :)

After looking at that it makes perfectly good sense to me to NOT use ls in a script!
I like scripts that do simple predictable stuff but, deleting kernel files??? I just would never go there. :)

Let's say the script deleted one of the kernel files in use and you reboot. :P Rut roh!

---

### Post by CharlesA on 2013-05-01
Well apt-get will ask you to confirm which packages you want to remove, but if you don't know what kernel you are running or what packages are installed, that could cause issues.

I'm usually booted into the latest kernel but I don't use PPAs or mainline kernels or whatever.

---

### Post by Cavsfan on 2013-05-01
> **CharlesA said:**
> Well apt-get will ask you to confirm which packages you want to remove, but if you don't know what kernel you are running or what packages are installed, that could cause issues.

I'm usually booted into the latest kernel but I don't use PPAs or mainline kernels or whatever.

Agreed. I only boot into the most recently installed kernel. I have never seen the need to use the previous kernel. 
At first I made the text file with the kernel files I got from looking at SPM but, now that I have been around a while I copy them and paste the file names from the terminal before they are installed as I mention in the first post.

That way one cannot go wrong. As long as you don't try to delete the kernel in use because then it will take 2 additional files: linux-headers-generic and  linux-image-generic with it.
If you do that and reboot you may as well plan on re-installing. :(

I have removed the latest kernel and re-installed it and that is fine as long as you do not reboot in between.

Did you know that the highest numbered kernel is not the one that you would boot into under certain circumstances?
I have deleted the latest one and installed a previous kernel and the previous one is what you will boot into.

It's not the higher the number that matters, it is the last one that is installed that matters.

---

### Post by Cavsfan on 2013-05-01
I am in Precise and am updating and can see that there is a new kernel to be installed. I entered **sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean**.
Which actually comes from a script that I *do* use daily - the two in blue on the first post.

Here is the output of [COLOR=#0000FF]ud[/COLOR]:
```
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Fetched 3,015 kB in 3s (867 kB/s)                 
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-generic linux-image-generic
The following packages will be upgraded:
  libgnutls26 linux-libc-dev
2 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 1,325 kB of archives.
After this operation, 5,120 B of additional disk space will be used.
Do you want to continue [Y/n]? 
```

Then after the 2 files get upgraded, I enter [COLOR=#0000FF]ud2[/COLOR] (which does **sudo apt-get dist-upgrade** again from the blue in the first post.
Here is the output from that:

```
cavsfan@cavsfan-desktop:~$ ud2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  [COLOR=#FF0000]linux-headers-3.2.0-41 linux-headers-3.2.0-41-generic linux-image-3.2.0-41-generic[/COLOR]
The following packages will be upgraded:
  linux-headers-generic linux-image-generic
2 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 51.2 MB of archives.
After this operation, 217 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
```

So before I enter Y and press enter I copy the file names (in red) above to my text file.

So my text file for Precise looks like this:

```
sudo apt-get purge linux-headers-3.2.0-37 linux-headers-3.2.0-37-generic linux-image-3.2.0-37-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-38 linux-headers-3.2.0-38-generic linux-image-3.2.0-38-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-39 linux-headers-3.2.0-39-generic linux-image-3.2.0-39-generic

sudo apt-get purge linux-headers-3.2.0-40 linux-headers-3.2.0-40-generic linux-image-3.2.0-40-generic

sudo apt-get purge linux-headers-3.2.0-41 linux-headers-3.2.0-41-generic linux-image-3.2.0-41-generic
```

I will reboot after the new kernel is installed and then delete the 39 kernel with the above command once I log back in and I will copy and paste "purged" by the 39 command.

Can it get any simpler than that? :)

---

### Post by Cavsfan on 2013-05-01
So, now I have rebooted and am using the 41 kernel (as you can see from the top right in the conky) and will delete the 39 kernel.

[[IMG]http://ompldr.org/taWE4cg[/IMG]]("http://ompldr.org/vaWE4cg/Screenshot from 2013-05-01.png")

```
cavsfan@cavsfan-desktop:~$ [COLOR="#FF0000"]sudo apt-get purge linux-headers-3.2.0-39 linux-headers-3.2.0-39-generic linux-image-3.2.0-39-generic[/COLOR]
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.2.0-39* linux-headers-3.2.0-39-generic* linux-image-3.2.0-39-generic*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 217 MB disk space will be freed.
Do you want to continue [Y/n]? 
```

Enter "Y" and I am done. No maybes, no ifs, no uncertainties just deleting what I know should be deleted. ;)

---

### Post by schragge on 2013-05-02
> **CharlesA said:**
> I thought it wasn't a good idea to do stuff like that with ls?
[http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

Maybe I'm just missing the point. :)
Yes, it's not a good idea in general, but */lib/modules* has a well-defined semantics: it only contains subdirectories named after kernel versions, so it's perfectly safe to parse the output of *ls* here. Actually, probably [safer]("http://anonscm.debian.org/gitweb/?p=dpkg/dpkg.git;a=commitdiff;h=3d98111") than parsing output of *dpkg -l*. And to remove any doubts, you can run *ls* with the *-q* option:
```
sudo apt-get purge $(ls -I`uname -r` -qrv /lib/modules | sed '1d;s/^/^linux-.\\*-/')
```
This solution is universal in that it accounts for any installed kernels, even custom-built, and can be easily adjusted to keep any number of kernels, e.g. if you want to keep four kernels including the running one:
```
sudo apt-get purge $(ls -I`uname -r` -qrv /lib/modules | sed '1,3d;s/^/^linux-.\\*-/')
```
If all you want is to keep the kernel you are currently running, the following solution will also work:
```
sudo apt-get purge --only-upgrade '^linux-(headers|image|image-extra)-'{'[0-9]',`uname -r`+}
```

---

### Post by schragge on 2013-05-02
> **Cavsfan said:**
> If you do that and reboot you may as well plan on re-installing.Not necessarily. Booting from a live medium and re-installing the kernel either through [thread=1769482]Boot-Repair[/thread] or from [thread=1156240]chroot[/thread] is all you need in this case. And if you happen to have another Linux installed on the same machine in the dual-boot configuration even this is sometimes not needed as it's often possible to install a new kernel from inside another working Linux installation. If you know you way around chroot, it's usually much simpler than re-installing the whole system.

> **Cavsfan said:**
> It's not the higher the number that matters, it is the last one that is installed that matters.Well, quoting myself > **schragge said:**
> If the kernel you are currently running is not the latest installed version then you could add to this a precaution not to purge the running kernel:
```
sudo apt-get purge $(ls -I`uname -r` -rv /lib/modules | sed '1d;s/^/^linux-.\\*-/')
```
The output of ls may be sorted by modification time, too:
```
sudo apt-get purge $(ls -I`uname -r` -qt /lib/modules | sed '1d;s/^/^linux-.\\*-/')
```

---

### Post by Cavsfan on 2013-05-02
> **schragge said:**
> (I don't use Ubuntu myself)

;)

---

### Post by schragge on 2013-05-02
I'm using Debian:
```

[COLOR=green]$[/COLOR] lsb_release -idrc
[COLOR=green]Distributor ID: Debian
Description:    Debian GNU/Linux 7.0 (wheezy)
Release:        7.0
Codename:       wheezy[/COLOR]

```

[s]BTW, Ubuntu's just [updated]("http://lwn.net/Articles/549094/") kernel again.[/s] [highlight]Edit.[/highlight] Sorry, it's the yesterday update. I see now you already installed it.

---

### Post by Cavsfan on 2013-05-02
LOL! I'm playing with debian but not sure it will last very long:
```
Distributor ID:    Debian
Description:    Debian GNU/Linux 6.0.7 (squeeze)
Release:    6.0.7
Codename:    squeeze
```

My point was it is pretty easy to make serious system impacting decisions when you do not even use Ubuntu. :D

_I made the point of how simple this method was *one last time*_ and that is about all I am going to say about that.... :P

---

### Post by QIII on 2013-05-02
Thread closed at OP request

---

