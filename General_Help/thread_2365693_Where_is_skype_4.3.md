---
title: "Where is skype 4.3?"
date: 2017-07-09
forum: General Help
---

### Post by Rrory on 2017-07-09
Hi I have Ubuntu 17.04 Zesty Zapus, I had old Skype and need to download Skype 4.3 but when I click on 'install' from Ubuntu software center nothing happens. What is going on?

---

### Post by deadflowr on 2017-07-09
I've moved your post to it's own thread, as the Op of the other thread had a more general package installing problem:
reference sake:[https://ubuntuforums.org/showthread.php?t=2365653]("https://ubuntuforums.org/showthread.php?t=2365653")

as per skype 4.3, It has now been retired:
[https://www.skype.com/en/download-skype/skype-for-linux/]("https://www.skype.com/en/download-skype/skype-for-linux/")

Not sure what canonical partners is up to...

---

### Post by Rrory on 2017-07-09
Oh okay thanks, I downloaded the skype 64 for Debian and my Software center has it "skypeforlinux", but when I click on "Install" nothing happens
what's going on....?

I'm using Zesty Zapus
Rory

---

### Post by &amp;KyT$0P# on 2017-07-09
@Rrory Try [this method]("https://repo.skype.com/") instead.

---

### Post by wildmanne39 on 2017-07-09
I suspect it is a bug that you are having problems with, check out:

[https://ubuntuforums.org/showthread.php?t=2363659](https://ubuntuforums.org/showthread.php?t=2363659)

---

### Post by monkeybrain20122 on 2017-07-09
The software centre has a bug. In stead of the Sc, there are is a  better package manager.
```

sudo apt install synaptic
```

For installing downloaded deb by right click, in stall gdebi

```
sudo apt install gdebi
```

Right click your downloaded .deb, from properties make gdebi the default, then click to install. 

With these two you don't need the software centre.

---

### Post by wildmanne39 on 2017-07-09
It does have a bug but it has been fixed the solution is in the link I gave above. I to use the methods monkeybrain20122 mentions, but I use the terminal most of all.

---

### Post by Rrory on 2017-07-09
Halogen; with all the code I don't understand which to add or omit so when I copy and paste this: dpkg -s apt-transport-https > /dev/null || bash -c "sudo apt-get update; sudo apt-get install apt-transport-https -y"
 I got *command not found*    I need you to tell me as a non-programmer how to do this please,
thanks everyone, I kind of hate that Skype was sold to Mic..:(

---

### Post by deadflowr on 2017-07-10
apt-transport-https is already installed on Ubuntu. So you can ignore that one.

However curl might not be.
(Installing it is easy enough, though)
```
sudo apt-get install curl
```
Then just run the curl command: 
```
curl https://repo.skype.com/data/SKYPE-GPG-KEY | sudo apt-key add - 
```
This adds the keys needed.

Then add the repo so your system knows where and what to look for
```
echo "deb [arch=amd64] https://repo.skype.com/deb stable main" | sudo tee /etc/apt/sources.list.d/skype-stable.list 
```

Then run (or re-run) the apt-get update command and then try the install command
```
sudo apt-get install skypeforlinux -y 
```

---

### Post by Rrory on 2017-07-10
wow thank you for explaining so clearly, I did everything you said and then I got this message:
*E: Unable to locate package skypeforlinux*

I tried downloading again and opening with Ubuntu Software but again nothing happened.... I appreciate all your help with this. It's weird to me as I've had Ubuntu for years and am not used to problems! It works so well and smoothly:)

---

### Post by deadflowr on 2017-07-10
I hope you ran the command
```
sudo apt-get update
```
 after adding the key and repo source files.
and before trying to install the skypeforlinux package.

---

### Post by monkeybrain20122 on 2017-07-10
> **Rrory said:**
> wow thank you for explaining so clearly, I did everything you said and then I got this message:
*E: Unable to locate package skypeforlinux*

I tried downloading again and opening with Ubuntu Software but again nothing happened.... I appreciate all your help with this. It's weird to me as I've had Ubuntu for years and am not used to problems! It works so well and smoothly:)


Told you the Ubuntu Software centre doesn't work, there is a bug. Open your deb with gdebi. Skype's server appears to be down often.

---

### Post by Habitual on 2017-07-10
Skype 4.x was EOL'd on July 1, 2017
or due to be, or planning to be...

---

### Post by Rrory on 2017-07-10
okay I installed synaptic and gdebi, then set gdebi on properties. downloaded the package and opened and installed with gdebi. But on rebooting my computer I still have old Skype 4.3 there not the newer version. What did I do wrong? or what can I do please....help:(

---

### Post by monkeybrain20122 on 2017-07-10
> **Rrory said:**
> okay I installed synaptic and gdebi, then set gdebi on properties. downloaded the package and opened and installed with gdebi. But on rebooting my computer I still have old Skype 4.3 there not the newer version. What did I do wrong? or what can I do please....help:(
Because it is not called skype. It is called "skype for Linux beta". So you didn't "update" skype, but have two versions of it with different names. Just remove skype (4.3)

---

### Post by Rrory on 2017-07-10
okay, how do I do that, please
as in the  past I used the software center....

---

### Post by monkeybrain20122 on 2017-07-10
You are using Ubuntu with Unity? Search for Skype in the dash, there should be two Skypes coming up. Skype for Linux beta is the one you want. 

To remove the 4.3, you can either in the terminal 
```

sudo apt-get remove skype
```

Or, since you have installed synaptic, you may as well get used to its gui (it is very easy). Open synaptic, search for skype, then right click and choose "mark for removal", then click "apply"


BTW, apart from broken software centre, tray icons don't work in 17.04. You should have stuck to 16.04 LTS [Here ]("http://www.webupd8.org/2017/03/fix-dropbox-indicator-menu-not-working.html")is a work around for tray icons

---

### Post by monkeybrain20122 on 2017-07-10
> **Rrory said:**
> wow thank you for explaining so clearly, I did everything you said and then I got this message:
*E: Unable to locate package skypeforlinux*

I tried downloading again and opening with Ubuntu Software but again nothing happened.... I appreciate all your help with this. It's weird to me as I've had Ubuntu for years and am not used to problems! It works so well and smoothly:)

First of all "Ubuntu Software" is broken, it doesn't work. Secondly Skype is not in Ubuntu's repository. Get it at its own download site [https://www.skype.com/en/download-skype/skype-for-linux/downloading/?type=weblinux-deb](https://www.skype.com/en/download-skype/skype-for-linux/downloading/?type=weblinux-deb)


**Edited:** Rrory's post has disappeared?

---

### Post by Rrory on 2017-07-11
Yes, I'm using Zesty Zapus,  I see  both  old and new Skypes there. Okay I opened synaptic, and removed it. Now Skype for Linux beta opens Super! 
Thank you so much for being so patient and explaining everything so clearly. And I'll check the tray icon work around as well, thank you for that as well.
 I guess I should have been more conservative but I always upgrade and enjoy doing so.
 I am so grateful! I really love Ubuntu and am spoiled as things like this are really rare!

---

