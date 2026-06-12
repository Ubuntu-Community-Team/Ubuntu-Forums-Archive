---
title: "SSH Tunnel vs IPSEC/Remote Desktop"
date: 2008-03-15
forum: General Help
---

### Post by hebetude on 2008-03-15
My company uses the F5 Firepass system to allow users to VPN into their work PCs.  Since Firepass does not work with Ubuntu, I must virtualize windows to even login to the VPN.  From there I remote desktop, so as you can imagine once all the translation is done I'm left with the slowest possible connection to my work PC.

My work mostly involves connection to servers inside our network, so I ask how can I connect setup some sort of portal to my work network that doesn't involve me pulling down a windows desktop refresh 20times a second.  I have been able to ssh to home from work, but what I need is the reverse of that

is this even possible? it seems there are no limits to ssh so I cant imagine why this would be out of reach.

---

### Post by chris_nava on 2008-04-29
I used firepass without any trouble under Gutsy 32 bit but I'm having trouble getting it to install under Hardy 64 bit.  I'm getting two error messages.

-----
Firefox could not install this item because "install-ln..rdf" (provided by the item) is not well-formed or does not exist. Please contact the author about this problem.
[OK]
-----
Firefox could not install the file at 

https:{URL intentionally withheld by poster}

because: Unexpected installation error
Review the Error Console log for more details.
-203
[OK]
-----

I'll try it under Hardy 32 bit and report back.

---

### Post by chris_nava on 2008-04-29
No luck. I got the same error messages under Hardy 32 bit.

---

### Post by hebetude on 2008-04-30
DONT DELETE HARDY YET :/

That is a firefox 3 error message, firepass's super lame plugin doesn't work with ff3.  All you need to do is install ff2.  I believe I use the ff2 64bit version, but there are guides on how to install the ff2 32-bit if that doesnt work.

The other tools it installs work fine in the 64bit environment I didnt have to mess with them

---

### Post by chris_nava on 2008-05-03
No luck with FF2 under Hardy 64bit.  I'm getting a security violation and it says "click here to install the plugin manually."
Clicking brings up another download dialog results in the same message.

Going to try copying the plugin from my old Gutsy install next...

---

### Post by hebetude on 2008-05-03
I just double checked the ff2 I use, it looks like firepass only supports the 32bit version of FF2

---

### Post by chris_nava on 2008-05-04
Is it possible to run the 32bit FF under Hardy 64bit?

---

### Post by hebetude on 2008-05-05
Yes, [http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)
I have ff32 on Hardy 64bit

---

