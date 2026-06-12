---
title: "Office 2007 in wine - ntlm_auth"
date: 2007-04-18
forum: General Help
---

### Post by vlad_x2 on 2007-04-18
I try to install office 2007 in wine (tried both with the one from repository and from cvs) and I keep getting this message:
"err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path."
The installer crashes and I think that's why. I attached the full log if you want to take a look.
I have ntlm_auth 3.0.24 (:lolflag: I need 3.0.25) but I can't find a newer one :(.
Please help me!

---

### Post by cmost on 2007-04-18
Office 2007 is NOT supported in WINE at this time.  You can use Office versions 2003, XP (2002), 2000, or 97 if you like.

---

### Post by vlad_x2 on 2007-04-19
Ok, so I have to wait :-w

---

### Post by jwedekin on 2007-10-20
I will give $100 to the first person who gives me a stable way to emulate Microsoft OFfice 2007 on my Ubuntu machine.

I need office 2007...I have too many issues with Microsoft OS's

---

### Post by CM Xtasy on 2007-10-20
> **jwedekin said:**
> I will give $100 to the first person who gives me a stable way to emulate Microsoft OFfice 2007 on my Ubuntu machine.

I need office 2007...I have too many issues with Microsoft OS's

VirtualBox.  Install  a virtual Windows and install Office 2007 on it.

---

### Post by Erwin Criddle on 2008-03-25
Yeah, the easiest solution would be to install Windows XP in a virtual machine using Virtualbox and then install Office 2007 in it.

---

### Post by octoberdan on 2008-04-12
> **jwedekin said:**
> I will give $100 to the first person who gives me a stable way to emulate Microsoft OFfice 2007 on my Ubuntu machine.

I need office 2007...I have too many issues with Microsoft OS's

If you have to have office 2007 and can't instead use OpenOffice or a version of office that wine supports, follow this fantastic howto:
[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)
and then perhaps something like [https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization) if you don't want to look at windows xp.

Although I whole heartedly recommend using OpenOffice over a Microsoft Office, on the grounds of stability and freedom.... and personal liberation from the big M ;-). I don't believe Ubuntu has the full suite out of the box, so you might have to install it. If you just need a Word like program, Applications -> Office -> OpenOffice.org Writer. 
  
Money or no money, we're here for you.

---

### Post by octoberdan on 2008-04-12
Oh! Well someone wrote a install guide for Office2k7 on Wine: [http://wine-review.blogspot.com/2008/03/office-2007-on-linux-with-wine-install.html](http://wine-review.blogspot.com/2008/03/office-2007-on-linux-with-wine-install.html) worth checking out, I guess. There's more info here: [http://appdb.winehq.org/appview.php?iVersionId=4992](http://appdb.winehq.org/appview.php?iVersionId=4992)

---

