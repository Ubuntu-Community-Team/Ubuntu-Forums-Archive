---
title: "Ekiga and sipdiscount"
date: 2006-07-01
forum: General Help
---

### Post by Liakoni on 2006-07-01
I am trying to get Ekiga to work with sipdiscount . But when i try to make call to a phone (not PC ) i get a "Security Check failed" .

My account settings are these :
Accountname :sip.discount
registrar : sip1.sipdiscount.com
username : 'l*****'
password : '******'
Realm/Domain : sip1.sipdiscount.com
Stun : stun.ekiga.net 
( If i use stun.sipdiscount.com , i get abnormal call termination )

PC to PC calls seems to work fine .

Does anybody have any idea what is wrong ?

---

### Post by norri64 on 2007-02-07
Hi,
I had similar problems with VoipBuster (same corporation) and had a little fight with my Ekiga. After all I got it working for outgoing calls. So you might try similarily with sipdiscount.

I first set the STUN-server to stun.voipbuster.com. 

I first tried calling a known telephone number in the format with only sip:+complete tel.number. (Now you get the abnormal... message). 

After going through all settings several times I almost gave up but then googling for hours I found one more hint and changed the dialstring to 'sip:+123456789@sip.voipbuster.com' and punch the dial-button.

Tadaa, the call went through in good quality.

To call another voipbuster-user I just changed the telephonenumber in the dialstring to my friends voipbuster-name.

The only thing I haven't figured out yet is howto receive incomming calls from other voipbuster users. The opponent party allways gets a busy tone.

---

### Post by goobsoft on 2008-06-04
You don't need to add @sip.voipbuster.com when your voipbuster.com account is the default (bolded) account.  I stumbled on the same issue.

---

