---
title: "How do I reverse this command?"
date: 2007-12-19
forum: General Help
---

### Post by Ripfox on 2007-12-19
I thought I was going to have to install and use ndiswrapper on this laptop due to synaptic ouchpad issues with the broacom firmware, but I sorted it out...my problem is that I ran:

sudo rmmod bcm43xx

and then:

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
 
Now no matter what I do I cannot get the driver to load by enabling it under "restricted drivers manager"

I removed it from  /etc/modprobe.d/blacklist and rebooted but still wont light up again.
What next?:confused:

---

### Post by bodhi.zazen on 2007-12-19
What happens if you sudo modprobe bcm43xx

---

### Post by Ripfox on 2007-12-19
It seems nothing happens...

---

### Post by bodhi.zazen on 2007-12-19
Did it load ?

lsmod | grep bcm43xx

---

### Post by Ripfox on 2007-12-19
bcm43xx               127336  0 
ieee80211softmac       31360  1 bcm43xx
ieee80211              35656  2 bcm43xx,ieee80211softmac

But...no light!

---

### Post by Ripfox on 2007-12-19
Any Ideas?

---

### Post by Ripfox on 2007-12-19
Bump

---

### Post by josephmc on 2007-12-22
i've got the same problem. how do you reverse a ndiswrapper install? i can modprobe it manually but it won't load on boot.

not that my wireless is working anyway but i figure this is a good step.

i'm starting to really dislike ubuntu :mad:

---

### Post by dlegend on 2007-12-22
> **josephmc said:**
> i've got the same problem. how do you reverse a ndiswrapper install? i can modprobe it manually but it won't load on boot.

not that my wireless is working anyway but i figure this is a good step.

i'm starting to really dislike ubuntu :mad:

Add the line "bcm43xx" into /etc/modules and it should automatically load it for you on boot (I believe). Let me know if it doesn't.

---

### Post by Ripfox on 2007-12-22
I just wound up following through with the ndiswrapper install on that machine and it works fine, but good to know in case it ever arises again...duh, why didn't I think of that...:)

---

### Post by tomchuk on 2007-12-22
The command to reverse the line that you gave in your original post is:
```
sudo sed -i -e '/bcm43xx/d' /etc/modprobe.d/blacklist
```

This is a good point to bring up the fact that you should never issue a command that you do not understand, especially one that involves issuing commands as root or through sudo. The command you posted simply appends 'blacklist bcm43xx' to the file /etc/modprobe.d/blacklist. That will prevent your module from being loaded automatically. The command above uses sed to search for a line containing bcm43xx in /etc/modprobe.d/blacklist and deletes it. But as I'm just some random dude on the Internet, you shouldn't take my word for it :)

For the explanation of the command you ran (using sudo tee instead of a standard shell redirect), see 'Downsides of using sudo' on [this page](https://help.ubuntu.com/community/RootSudo)

For an explanation of the command I gave you, get a strong drink and check out `man sed' or `info sed'

---

### Post by josephmc on 2007-12-23
you could do that....i just wanted to revert it back to the original config. i doubt that's how ubuntu would load that module on a clean install. thanks tho!

---

### Post by tomchuk on 2007-12-23
> **josephmc said:**
> you could do that....i just wanted to revert it back to the original config. i doubt that's how ubuntu would load that module on a clean install. thanks tho!

Removing the line from blacklist will result in Ubuntu loading bcm43xx in the exact same way as before the module was blacklisted -- that is by detecting the hardware and loading the corresponding module.

---

### Post by Ripfox on 2007-12-23
Actually, I removed it from /etc/modprobe.d/blacklist manually...it was the first thing I tried. It did not work, as you have to go back and put bcm43xx back into /etc/modules for it to completely reverse the effect. It was not that I did not understand what the command did, I have used it many times before to blacklist that module. I just spaced putting it back into /etc/modules. :)

---

