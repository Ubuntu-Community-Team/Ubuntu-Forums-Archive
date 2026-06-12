---
title: "Amule: installing on 18.04 LTS"
date: 2020-12-04
forum: General Help
---

### Post by 0georgebaldwin0 on 2020-12-04
Apologies in advance for asking stupid questions:


I have recently installed  18.04 LTS with the Budgie desktop environment and am trying to install Amule but with little success. Ironically, I have 16.04 LTS with Amule working perfectly on a legacy hard drive on the same machine. I have tried looking for an appropriate deb download and thought that I had found it here: [https://ubuntu.pkgs.org/18.04/ubuntu-universe-amd64/amule_2.3.2-2_amd64.deb.html](https://ubuntu.pkgs.org/18.04/ubuntu-universe-amd64/amule_2.3.2-2_amd64.deb.html) 

Now for the stupid stuff - when I follow the instructions to update the package index and then install the deb package I get the following result: 

*E: Unable to locate package amule_2.3.2-2_amd64.deb**E: Couldn't find any package by glob 'amule_2.3.2-2_amd64.deb'*
*E: Couldn't find any package by regex 'amule_2.3.2-2_amd64.deb'*

I thought this was because the repository wasn't added but when I checked, I got:

[I]'universe' distribution component is already enabled for all sources.
[/I]
...soooo, I'm assuming that I've got the right repository but I'm obviously missing something, um, obvious.....

I'd be really grateful for any advice on this,

MTIA

---

### Post by howefield on 2020-12-04
What was the command that you used to install of amule.

Are you trying to install a downloaded deb package ?

If so, something like

```
sudo apt install /home/george/Downloads/amule_2.3.2-2_amd64.deb
```

assuming that the filename, where the downloaded deb package has been stored and your username is as above ;)

---

### Post by 0georgebaldwin0 on 2020-12-04
Tks Howefield!

....but no joy as yet, I'm now getting this output when I plug in the path, ie:

[I]sudo apt install /home/Downloads/amule_2.3.2-2_amd64.deb

E: Unsupported file /home/Downloads/amule_2.3.2-2_amd64.deb given on commandline


[/I]I just tied the the software installer that comes with budgie and I get the message[I] 

" The following packages have unmet dependencies" [/I]but no indication of what these might be. Is there a way to easily  establish this from the terminal? I did find Stackoverflow but I'm a bit nervous of playing with stuff I don't understand. Would you think it's worth a try?

[FONT=courier new]"Try follow this step 1 by 1[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]apt-get autoclean[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]apt-get -f install[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]dpkg --configure -a[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]apt-get -f install[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]apt-get -u dist-upgrade[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]or try "aptitude" instead of "apt-get"[/FONT]

---

### Post by CelticWarrior on 2020-12-04
> **0georgebaldwin0 said:**
> Tks Howefield!

....but no joy as yet, I'm now getting this output when I plug in the path, ie:

[I]sudo apt install /home/Downloads/amule_2.3.2-2_amd64.deb

E: Unsupported file /home/Downloads/amule_2.3.2-2_amd64.deb given on commandline


[/I]I just tied the the software installer that comes with budgie and I get the message[I] 

" The following packages have unmet dependencies" [/I]but no indication of what these might be. Is there a way to easily  establish this from the terminal? I did find Stackoverflow but I'm a bit nervous of playing with stuff I don't understand. Would you think it's worth a try?

[FONT=courier new]"Try follow this step 1 by 1[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]apt-get autoclean[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]apt-get -f install[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]dpkg --configure -a[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]apt-get -f install[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]apt-get -u dist-upgrade[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]or try "aptitude" instead of "apt-get"[/FONT]

No no no...

You can (and should) make sure your package management system is fine and fully updated before installing any new software:
```
sudo apt update && sudo apt full-upgrade
```
Post here any errors. If no errors then 1) check whether the universe repository is enabled (open Software & Updates) because amule is there (for 18.04) and then 2) simply
```
sudo apt install amule
```
Software in the repositories can and should be installed online, not by downloading the .deb.

---

### Post by howefield on 2020-12-04
> **0georgebaldwin0 said:**
> sudo apt install /home/Downloads/amule_2.3.2-2_amd64.deb

E: Unsupported file /home/Downloads/amule_2.3.2-2_amd64.deb[/code]

There should be a username between home and Downloads in your command above. Also, it is useful to copy/paste the entire terminal input and output (between code tags) to better help others to help you.

> The following packages have unmet dependencies" [/I]but no indication of what these might be. Is there a way to easily  establish this from the terminal? I did find Stackoverflow but I'm a bit nervous of playing with stuff I don't understand. Would you think it's worth a try?

None of those steps is likely to make the situation worse, but I'd start with a 

```
sudo apt update && sudo apt upgrade
```

then report back any errors. 

> [FONT=courier new]"Try follow this step 1 by 1[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]apt-get autoclean[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]apt-get -f install[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]dpkg --configure -a[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]apt-get -f install[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]apt-get -u dist-upgrade[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]or try "aptitude" instead of "apt-get"[/FONT]

---

### Post by deadflowr on 2020-12-04
> Now for the stupid stuff - when I follow the instructions to update the package index and then install the deb package I get the following result:

E: Unable to locate package amule_2.3.2-2_amd64.debE: Couldn't find any package by glob 'amule_2.3.2-2_amd64.deb'
E: Couldn't find any package by regex 'amule_2.3.2-2_amd64.deb'

From this it seems like you tried installing it like
```
sudo apt install amule_2.3.2-2_amd64.deb
```
drop the _2.3.2-2_amd64.deb and leave it as just amule.
```
sudo apt install amule
```
the package version string is not needed.

---

### Post by CelticWarrior on 2020-12-04
It seems @howefield and @deadflowr are saying the same as I did which is fine.

[B]In summary, as long as you have the Universe repository enabled, just install aMule like any other software. 
[/B]
Now, having said that, here's the bad news: Years ago I helped someone with aMule installed like we're telling you to just to find out the version in the 18.04 repo is hopelessly broken. Unless it has been fixed you may notice the main windows doesn't open and running it from terminal may show the following error:
```
*amule crashed with SIGSEGV in wxWindow::DoClientToScreen()*
```

That being the case please come back here. I can give a solution but I must, preemptively, warn you it's anything but easy as it implies compiling from source two sets of code and editing a .cpp file. You should understand the method of installing software from the repos is barely a "level 1" whereas what you need to do if that one doesn't work takes it up at least to "level 11".

Perhaps better stick with torrents :mrgreen: 
Transmission is already installed and works beautifully.

---

### Post by 0georgebaldwin0 on 2020-12-04
Hmmm,

After a huuuuge upgrade download, I checked that the Universe repository is enabled and then tried: [COLOR=#000000][FONT=&quot]sudo apt install amule

[/FONT][/COLOR]I now get:

```
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 amule : Depends: amule-common (= 1:2.3.2-2) but 1:2.3.2-6 is to be installed
         Recommends: amule-utils but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

[FONT=arial]CW: you certainly know how to sell! Level 11 sounds like about 10.95 too high for me. I really do like Amule though so if there is any way that isn't a guaranteed fail for me then I'd like to at least have a look....torrents???[/FONT]

---

### Post by deadflowr on 2020-12-05
We would need the full output from the commands Celticwarrior and howefield posted,
as well as output from
```
sudo apt install -f
```
for good measure.

---

### Post by 0georgebaldwin0 on 2020-12-05
Thanks to all for your help and support so far.

Whilst I can of course post the outputs from your suggestions, I'm now wondering whether I'm simply barking up the wrong end of the stick (without a paddle) when it comes to both Budgie and 18.04......

I've now uncovered some functionality problems with the Budgie desktop that make my original reasons for choosing it look wrong. I have also done some reading about 18.04 and I'm getting the distinct impression that 20.04 is an improvement and that there are fewer problems with Amule as well.

This whole sorry saga was prompted by my wanting to ditch 16.04 Mate (where everything worked instantly)  on a mechanical drive dual-booting Windows and move to discrete SSDs for both OS and Data. I've had a number of problems with the dual-boot, caused by windows doing what what it does best (i.e f*** all) and some white knuckle rides thinking that I'd lost my data, so the 3 drive solution seemed to be sensible. TBH, the lightweight requirement was more a function of me happening to already have a 30gb microSSD installled on my laptop. I did start by trying LinuxLiteOS but somewhat surprisingly (to me anyway) I ran out of space very quickly and it seemed to be a fairly restricted environment....hence my return to the Ubuntu fold - the Budgie install has left me with bags of room, so now I'm thinking that perhaps I should just be looking at Mate once again only this time on 20.04

I'd appreciate it very much if you'd share any thoughts on the above,

All gifts gratefully received;)

GB

---

### Post by 0georgebaldwin0 on 2020-12-06
Just wanted to thank everyone who's spent time trying to help.

I decided to try 20.04 Mate on another drive and it's been fine for everything (so far!) and whilst it's a couple of seconds bit slower than 18.04 Budgie I have the functionality I need so all is rosy in the garden. 
I'm just going to give up on both 18.04 altogether and take another look at Budgie in a few releases.

Thanks once more - I'm not sure I'll be back any time soon as I never had any problems at all with 16.04 Mate in close to 5 years):P

---

