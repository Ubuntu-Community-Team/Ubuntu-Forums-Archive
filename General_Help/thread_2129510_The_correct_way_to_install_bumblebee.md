---
title: "The correct way to install bumblebee??"
date: 2013-03-26
forum: General Help
---

### Post by NikiNfOuR on 2013-03-26
Dear friends, as they always say i too dig a lot of times before posting, but my samsung laptop which runs on ubuntu gnome remix edition 12.10 which has an nvidia GT 650M graphic card was not able to install bumblebee not once but twice. Being a beginner i had to reinstall the OS twice!! Can any one help me on how to properly install bumblebee on my laptop so that i can use my onboard GPU instead of nvidia so that i can have good battery backup?? :)

Also i have one more doubt, My laps temperature is increasing than usual, is this because the lap is currently using nvidia GPU??? ( cos lap is new... )

---

### Post by slickymaster on 2013-03-26
To add the stable Bumblebee PPA and install Bumblebee open a terminal window and run the following commands:
```
sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia
```
Once installed, log out and log back in, then try it out by running **optirun glxspheres**. You may need to edit the Bumblebee configuration file if you're not using nvidia-current (**/etc/bumblebee/bumblebee.conf**).

Then, if you want an application or game to use the Nvidia graphics card, launch it with [B]optirun
[/B]Example:```
optirun steam
```

---

### Post by NikiNfOuR on 2013-03-26
I have installed like this only, twice...... but didn't work!!

but in one site i saw  after sudo apt-get update they types

[COLOR=#000000][FONT=Tahoma]sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic!! they says it's important to install the graphic drivers, is it true???[/FONT][/COLOR]

---

### Post by slickymaster on 2013-03-26
> **NikiNfOuR said:**
> I have installed like this only, twice...... but didn't work!!

but in one site i saw  after sudo apt-get update they types

[COLOR=#000000][FONT=Tahoma]sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic!! they says it's important to install the graphic drivers, is it true???[/FONT][/COLOR]

Did you edit your **/etc/bumblebee/bumblebee.conf** file?
In this file check the following:
**KernelDriver=nvidia-current** is correct if you have installed the nvidia-current package, you should not change that on Ubuntu.
Since Ubuntu 12.10, you need to install the kernel headers yourself. If you have changed this to **KernelDriver=nvidia **revert your KernelDriver change (the Driver= one does not matter) and install the kernel headers:
```
sudo apt-get install linux-headers-generic
```
This should automatically build the nvidia module. When this is completed, reboot or start the Bumblebee daemon:
```
sudo start bumblebeed
```
Then try running
```
optirun glxspheres
```

---

### Post by NikiNfOuR on 2013-03-26
I have installed the linux-generic-headers!! So can i install the bumblebee as you instructed in the first post???

---

### Post by slickymaster on 2013-03-26
Yes, I believe you can. You did check your** /etc/bumblebee/bumblebee.conf** file, didn't you?

---

### Post by NikiNfOuR on 2013-03-26
But i haven't installed bumblebee yet!! How can i look for a file which i am not suppose to find??? It is not there. I told you, i am now running a freshly installed ubuntu gnome remix edition from today morning!!

---

### Post by slickymaster on 2013-03-26
I was under the impression that you had already installed it. No problem, now that you installed linux-headers-generic, just go ahead and install bumblebee like I described in my first post.

---

### Post by NikiNfOuR on 2013-03-26
Thanks friend, i will post after it is complete... hope you will be here if something comes up... :)

---

### Post by slickymaster on 2013-03-26
I'll hope that everything will go smoothly.
If not me, I'm sure there will be plenty of other people that will be more than willing to help you.

---

### Post by NikiNfOuR on 2013-03-26
I know u or others will help me :) Thats why i love ubuntu and it's community sooooooooo much :) Thanks for the help, everything went out fine, but only one more  thing, how do you insert the code area when you are replying in the forum?? Didin't i say i was a beginner??

---

### Post by slickymaster on 2013-03-27
Glad you got it fixed.

You have to ways two ways to insert a code area in a reply, or in any post for that matter.
One way is to select the text you wish to be within the code box and then click the **#** at the top of the post box, to the left of <>.
The other way is to do it manually by _putting **code** between square bracktes_ at the beginning of the text you wish to be within the code box and _putting **/code** between square brackets_ at the end of it.

It´s all explained [here]("http://ubuntuforums.org/misc.php?do=bbcode").

---

### Post by NikiNfOuR on 2013-03-27
> **slickymaster said:**
> Glad you got it fixed.

You have to ways two ways to insert a code area in a reply, or in any post for that matter.
One way is to select the text you wish to be within the code box and then click the **#** at the top of the post box, to the left of <>.
The other way is to do it manually by _putting **code** between square bracktes_ at the beginning of the text you wish to be within the code box and _putting **/code** between square brackets_ at the end of it.

It´s all explained [here]("http://ubuntuforums.org/misc.php?do=bbcode").


Thanks for the reply mate... Very much appreciated... cheers... :)

---

