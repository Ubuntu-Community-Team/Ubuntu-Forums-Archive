---
title: "Installing pepper flash but which commands are correct?"
date: 2016-01-27
forum: General Help
---

### Post by Buntu Bunny on 2016-01-27
Now that Google is dropping support for Chrome in 12.04, I've installed Chromium. I'm wanting to install pepper flash, but have found three different sets of instructions at various sites. Commands for installing the installer are all the same:

```
sudo add-apt-repository ppa:skunk/pepper-flash
sudo apt-get update
sudo apt-get install pepflashplugin-installer
```

What's different is what is to be added to the configuration file after the CHROMIUM_FLAGS="" line. My questions are

1. What's the difference between 

```
. /usr/lib/pepflashplugin-installer/pepflashplayer.sh
```

```
echo ". /usr/lib/pepflashplugin-installer/pepflashplayer.sh" | sudo tee -a /etc/chromium-browser/default
```

and

```
sudo vi /etc/chromium-browser/default
CHROMIUM_FLAGS="$CHROMIUM_FLAGS --ppapi-flash-path=/usr/lib/pepflashplugin-installer/libpepflashplayer.so --ppapi-flash-version=$FLASH_VERSION"
```

2. Which one should I use?

---

### Post by v3.xx on 2016-01-28
Hi Buntu Bunny :D

I haven't mess with pepper in a while.  Is installing it from the repositories not the way to go anymore?

---

### Post by Bashing-om on 2016-01-28
Buntu Bunny; Hey, hey ..

Long time no see.
in 12.04 what returns:
```

apt-cache show pepperflashplugin-nonfree

```
If you install it from repo:
```

sudo update-pepperflashplugin-nonfree

```
may prove helpful to get pepperflash to work.

As our friend v3.xx notes; why do it the hard way ?

[INDENT]if it is hard
[INDENT][INDENT][INDENT]doing something wrong
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by v3.xx on 2016-01-28
Buntu and Bashing

Let the good times roll :D

---

### Post by monkeybrain20122 on 2016-01-28
[ajgreeny]("http://ubuntuforums.org/showthread.php?t=2311381&p=13429722#post13429722") pointed out that the package pepperflashplugin-nonfree is deprecated (it is an ugly hack that downloaded Chrome and then extract pepper-flash) now you just need to install adobe-flashplugin from the Partner's repo to get the latest pepperflash. More [here]("https://wiki.ubuntu.com/Chromium/Getting-Flash"). This should work in Chromium out of the box. For it to work for Firefox you need freshplayerplugin from webupd8's ppa[ https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8/+index?batch=75&memo=75&start=75]("https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8/+index?batch=75&memo=75&start=75")

---

### Post by Buntu Bunny on 2016-01-28
> **v3.xx said:**
> Hi Buntu Bunny :D

I haven't mess with pepper in a while.  Is installing it from the repositories not the way to go anymore?

> **Bashing-om said:**
> Buntu Bunny; Hey, hey ..

Long time no see.
in 12.04 what returns:
```

apt-cache show pepperflashplugin-nonfree

```

v3.xx, hey! Thank you for responding. I was thinking I'd have to bump the thread. :)

Hey Bashing-om, it *has* been awhile!

I get this

```
BuntuBunny@BuntuBunny-CM1740:~$ apt-cache show pepperflashplugin-nonfree
N: Can't select versions from package 'pepperflashplugin-nonfree' as it is purely virtual
N: No packages found
```

From what I understand, pepper flash installer is in the 14.04 repos but not 12.04, hence the manual install. 

I believe one of those codes is for automatically updating the version of pepper flash, but I don't read code well enough (plus rarely know what I'm doing with it anyway :o ) to feel confident as to which one of the above three I should use to modify the pepper flash config file. I'm hoping someone here can give me a clue.

> **monkeybrain20122 said:**
> [ajgreeny]("http://ubuntuforums.org/showthread.php?t=2311381&p=13429722#post13429722") pointed out that the package pepperflashplugin-nonfree is deprecated (it is an ugly hack that downloaded Chrome and then extract pepper-flash) now you just need to install adobe-flashplugin from the Partner's repo to get the latest pepperflash. More [here]("https://wiki.ubuntu.com/Chromium/Getting-Flash").

Monkeybrain I missed your comment until after I hit the publish button. I will look into your link. From what I've read, the above codes will work as long as I have Chrome installed first (as it actually has pepper flash). I already have Chrome, but will be abandoning it because Google is abandoning it for 12.04.

---

### Post by monkeybrain20122 on 2016-01-28
The adobe-flashplugin package is backported to 12.04. You can just install that. [URL="https://launchpad.net/ubuntu/+source/adobe-flashplugin"]https://launchpad.net/ubuntu/+source/adobe-flashplugin

[/URL]> From what I've read, the above codes will work as long as I have Chrome installed first 

I think you are confusing freshplayerplugin with this. freshplayerplugin is a wrapper for pepper-flash for Firefox, it will work as long as you have pepper-flash in your system and in its path, so if you have Chrome it will work automatically. But even if you don't, it will work if you have pepperflash.so somewhere it can find, e.g by installing the adobe-flashplugin package (or pepperflashplugin-nonfree before)

---

### Post by Buntu Bunny on 2016-01-28
> **monkeybrain20122 said:**
> The adobe-flashplugin package is backported to 12.04. You can just install that. [URL="https://launchpad.net/ubuntu/+source/adobe-flashplugin"]https://launchpad.net/ubuntu/+source/adobe-flashplugin

[/URL]

I think you are confusing freshplayerplugin with this. freshplayerplugin is a wrapper for pepper-flash for Firefox, it will work as long as you have pepper-flash in your system and in its path, so if you have Chrome it will work automatically. But even if you don't, it will work if you have pepperflash.so somewhere it can find, e.g by installing the adobe-flashplugin package (or pepperflashplugin-nonfree before)

Well, I haven't run across anything about freshplayerplugin, probably because I don't care about Firefox. Like I said, I want pepper flash for Chromium.

---

### Post by v3.xx on 2016-01-28
I still have 12o4 installed.  I use it as backup these days.  If you don't mind me asking; why are you?

---

### Post by deadflowr on 2016-01-28
> **Buntu Bunny said:**
> Well, I haven't run across anything about freshplayerplugin, probably because I don't care about Firefox. Like I said, I want pepper flash for Chromium.
Enable the canonical partner repository and simply install the adobe-flashplugin package.
As pointed out the whole shebang has been backported to 12.04, including pepper.

the adobe-flashplugin package now contains both the regular, if really old, flash plugin and the current pepper flash plugin.

---

### Post by Dennis N on 2016-01-29
Yes^^^

Just installed Chromium on Ubuntu 12.04. Enabled "Canonical Partners" in Synaptic Package Manager (Settings > Repositories > Other Software > checkbox: Canonical Partners; Reload; search "adobe-flashplugin"; mark and install. Restart Chromium and plugin detected.
Tested at [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)
Version 20.0.0.267

Working fine.

---

### Post by Buntu Bunny on 2016-01-29
> **deadflowr said:**
> Enable the canonical partner repository and simply install the adobe-flashplugin package.
As pointed out the whole shebang has been backported to 12.04, including pepper.

the adobe-flashplugin package now contains both the regular, if really old, flash plugin and the current pepper flash plugin.

> **Dennis N said:**
> Yes^^^

Just installed Chromium on Ubuntu 12.04. Enabled "Canonical Partners" in Synaptic Package Manager (Settings > Repositories > Other Software > checkbox: Canonical Partners; Reload; search "adobe-flashplugin"; mark and install. Restart Chromium and plugin detected.
Tested at [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)
Version 20.0.0.267

Working fine.

Whew, thank you both! The explanations were helpful and much appreciated. This thread started after I read another recent thread about Google no longer supporting Chrome in 12.04. The advice there was that pepper flash must be manually installed for Chromium in 12.04. I'm glad I took time to research and ask about what puzzled me. What confused me here, was that I enabled the Canonical Partners repository ages ago, and Software Center told me adobe-flashplugin was already installed. This morning I marked it for installation in Synaptic, it did its thing, and Chromium does exactly what I need it to do. 

Again, thank you! Now going to mark this thread as solved.

---

### Post by Bashing-om on 2016-01-29
Buntu Bunny; :)

> 
 This morning I marked it for installation in Synaptic, it did its thing, and Chromium does exactly what I need it to do. 


[INDENT][INDENT]when you are good
[INDENT][INDENT][INDENT]YOU are good
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by echotech2 on 2016-01-30
> **Bashing-om said:**
> Buntu Bunny; :)



[INDENT][INDENT]when you are good
[INDENT][INDENT][INDENT]YOU are good
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

  Did you mean when he's bad he's still pretty good?

---

