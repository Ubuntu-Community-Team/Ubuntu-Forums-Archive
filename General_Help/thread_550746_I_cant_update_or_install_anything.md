---
title: "I cant update or install anything"
date: 2007-09-14
forum: General Help
---

### Post by jrmink on 2007-09-14
Errors after install that always include "gparter" I cant updating or install anything
--------------------------------------------------------------------------------

I run the update manager and this error message comes up-

"Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

I then try to run the Add/Remove application under the application tab and I get the following error.

Failed to check for installed and available applications

"This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

Anyone have any suggestions or fixes for this problem?  When I burned the cd I burned it at 8x speed and did not check the disc before I installed. I would rather not have to reinstall though... 

I am completely new to linux and have just switched over from 10 years of windows xp so I am a complete noob.  If someone could please help me have a better transition into linux that would be great.

jrmink
thanks
__________________

---

### Post by Sef on 2007-09-14
> When I burned the cd I burned it at 8x speed and did not check the disc before I installed.

Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")?  If not, then you could have a bad download.    Redownload and md5sum.

Burn at 4x or less.   Faster can corrupt the burn.

---

### Post by jrmink on 2007-09-14
That is probably it but is there anything else it could possibly be?

---

### Post by jrmink on 2007-09-18
I got it working btw and for people that might come across this post you must take all precautions when buring the disc (do it at 4x) then md5sum or w/e and also check disc once you load it up.  It worked for me after I made sure I burned the cd right.

---

