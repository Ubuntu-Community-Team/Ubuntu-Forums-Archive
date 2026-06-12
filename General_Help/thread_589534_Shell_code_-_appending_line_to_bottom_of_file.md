---
title: "Shell code - appending line to bottom of file"
date: 2007-10-24
forum: General Help
---

### Post by utopial on 2007-10-24
i have a shell script that wipes then reinstalls my sound files. however, it also removes an important line from one of those files. i was wondering if someone can help me with the code to add that line back to the bottom of that file?

my code to wipe/reinstall sound is:

```
#!/bin/bash
echo XXXXXX | sudo -S su -c 'yes | apt-get --purge remove linux-sound-base alsa-base alsa-utils'

sudo apt-get install linux-sound-base alsa-base alsa-utils gdm 
```

where xxxxx = my password

how do i then incorporate the script from [http://ubuntuforums.org/showpost.php?p=2437566&postcount=552](http://ubuntuforums.org/showpost.php?p=2437566&postcount=552)?
ie
add the following code to the bottom of /etc/modprobe.d/alsa-base 
```
options snd-emu10k1 enable=1
```

then run this:
```
sudo update-modules
sudo modprobe snd-emu10k1
```

thanks

---

### Post by mahousaru on 2007-10-24
The easiest way to append any text to a file is to use >>

A single > means overwrite and >> means append.

As a test try this

```


echo "options snd-emu10k1 enable=1" >> /tmp/testfile.log
cat /tmp/testfile.log


```

each time you run the script it should add another line so u should see it growing.

---

### Post by utopial on 2007-10-26
thanks
i tried it out but got 'permission denied'
any idea why? i had already logged in as sudo

```
sudo echo "options snd-emu10k1 enable=1" >> /etc/modprobe.d/alsa-base

bash: /etc/modprobe.d/alsa-base: Permission denied
```

---

### Post by mahousaru on 2007-10-26
Hmmm I guess the redirect is loosing the sudo rights elevation.  I jsut tried it myself and I get the same error as you.  

The only quick way I can think around it apart from giving your account rights to the file is to create a script with the redirect in it and then sudo /nameofscript

That should wrap sudo around the redirect within the script session

---

### Post by taurus on 2007-10-26
```
sudo echo "options snd-emu10k1 enable=1" >> **sudo** /etc/modprobe.d/alsa-base
```

---

### Post by mahousaru on 2007-10-26
@taurus - hee hee I didn't think to sudo the pipe *headbutts keyboard*

---

### Post by #Reistlehr- on 2007-10-26
you need to use

echo "line" | sudo tee -a FILENAME

---

### Post by utopial on 2007-10-27
thanks guys. #Reistlehr-  your solution worked great. thanks a heap

---

