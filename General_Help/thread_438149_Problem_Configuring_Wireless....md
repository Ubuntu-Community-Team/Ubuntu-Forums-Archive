---
title: "Problem Configuring Wireless..."
date: 2007-05-09
forum: General Help
---

### Post by Brightbelt on 2007-05-09
Hi,
I've set up my laptop to dual boot Vista Home Premium 32-bit/Ubuntu Linux (Feisty Fawn). I'm trying to configure my wireless on the Ubuntu System, and it gives me several WEP choices to choose and then type a password...
 
The problem is: I think Ubuntu is wanting a pass phrase ( I remember when I set up my Linksys, the Linksys Tech Rep gave me a one-time pass-phrase which I have never needed to use since) because it's only allowing 15 to 16 characters in the password field. My normal password with which I connect from Windows is something like a 26 character password.  I always use my 26 character password to connect to the network. (I have the password of course, but not the pass-phrase given by the Linksys Tech Rep)
 
None of the WEP choices (and I know that's my encryption mode) in Ubuntu allow more than 15 to 16 characters. Does this mean that Ubuntu is incompatible with this Linksys wireless network?
 
I appreciate any assistance,...Thanks,  Frank

---

### Post by jimbob on 2007-05-09
If you are using a 26-character password in Vista and it works then that must be the password that is currently stored in your Linksys router also and is what you must enter into Ubuntu in order for it to work.

WEP is very weak encryption and can be easily broken so as an aside I would recommend that you go to WPA1/2 if at all possible.

I haven't used WEP in some time but as I remember in Ubuntu it gives you a choice of hex or ascii characters in the password field.  If you enter 13 ascii characters in this field that is the same as 26 hex (4-bit) characters in the field.  Go into your Vista machine and see what that password is and duplicate it in  Ubuntu and it should work for you.  Make sure that the generate passphrase is not selected in Ubuntu.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Brightbelt on 2007-05-09
Thanks for responding Jimbob.

I know what my 26  character password is -- the point is that no matter WHICH WEP scenario I choose in Ubunto (hex or ascii etc), the password field stops me at 15 or 16 characters and I cannot enter a 26 character password, no matter which scenrio I choose in Linux. 

I've actually tried entering this password in ALL of the choices Ubuntu offers. 

Am I missing something from your response or are we on the same page?

Many Thanks, Frank

---

### Post by dfreer on 2007-05-09
correct me if I'm wrong, but the way I always saw it was that there were TWO passwords. One is the passphrase that the user enters, and the other is a hash of numbers that represents that passphrase. the router only accepts the hash, and to make things eaiser for windows users, windows will automatically take the passphrase that the user enters and converts it to the hash. Ubuntu expects you to type the hash in directly. 

I'm probably wrong, but the easiest way to check is to log into your router, check the wireless security tab out, and see what is entered in there. On my netgear router I'm pretty sure it has the passphrase typed in one box, and then below it shows the actual hash that represents that passphrase. sorry if I sound like an idiot, but I'm going off the top of my head.

EDIT: if you are going to be using security it is better that you use WPA instead of WEP, so this might be a good chance to change your password anyways.

---

### Post by jimbob on 2007-05-09
I would take dfreer's (and my) advice and go with WPA2 unless you have a compelling reason not to do so.   I know Vista will offer that choice but will your router?

What software are you using in Ubuntu to do this - network manager?  I gave up on that and am using Wicd which seems to be a much better package.

Try to get Vista and the router working together via WPA2 and then tackle Ubuntu.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by stchman on 2007-05-09
> **Brightbelt said:**
> Hi,
I've set up my laptop to dual boot Vista Home Premium 32-bit/Ubuntu Linux (Feisty Fawn). I'm trying to configure my wireless on the Ubuntu System, and it gives me several WEP choices to choose and then type a password...
 
The problem is: I think Ubuntu is wanting a pass phrase ( I remember when I set up my Linksys, the Linksys Tech Rep gave me a one-time pass-phrase which I have never needed to use since) because it's only allowing 15 to 16 characters in the password field. My normal password with which I connect from Windows is something like a 26 character password.  I always use my 26 character password to connect to the network. (I have the password of course, but not the pass-phrase given by the Linksys Tech Rep)
 
None of the WEP choices (and I know that's my encryption mode) in Ubuntu allow more than 15 to 16 characters. Does this mean that Ubuntu is incompatible with this Linksys wireless network?
 
I appreciate any assistance,...Thanks,  Frank

Uncheck all the enable boxes in Administration--->Networking under all teh devices.  Let network-manager handle these duties.  Once done then proceed.  When you click on network-manager in the notification area a list of available wireless networks should drop down.  Select yours and then supply the WEP key.

I am with the others use WPA ro WPA2 for your wireless encryption.

---

### Post by palmtree on 2007-05-09
I have the same problem configuring my WEP for Ubuntu. When I tried 128 Bit WEP only some of the 26 hexidecimal characters can be entered, hence no go. I then changed to 64 bit and was able to put in the hex as it had only 8 or 10 hex characters. Incidently, I used WiFi Radar when I was using Ubuntu 6.10 and was able to configure WEP with the 26 Characters!! WiFi radar on 7.04 seems flakey and I haven't able to use it. I realize how insecure WEP is and I would like to use WPA, but I am unclear if Ubuntu supports WPA without some significant frigging. Is that the case?

---

### Post by Brightbelt on 2007-05-09
Ok Guys,
  I've got my wireless reconfigured to WPA Personal with a new password.  I've got it working on my laptop with XP and it's also set fine on the Vista in my dual boot laptop with Ubuntu.

Now...I've tried setting it up in Ubuntu and I've typed in EVERYTHING in every field that it asks...I chose 'WPA Personal' in the drop down menu, set the type to TKIP, put in the Network Name, typed in the password, then....

Ubuntu tries to connect for a while - it really tries - but then it doesn't connect. If I have to use a different method, how would I do this?

Why won't it work this way? I was able to restart, go to Vista and set it up in seconds....

Many Thanks for further assistance, Frank

---

### Post by jimbob on 2007-05-09
As you may have gathered I am no fan of Network Manager.

If I was you I'd back it out (apt-get remove --purge network-manager) and download and install Wicd.  

Get it from here:  [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

You can always re-install network-manager if you don't like it.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by AbredPeytr on 2008-02-15
> **jimbob said:**
> As you may have gathered I am no fan of Network Manager.

If I was you I'd back it out (apt-get remove --purge network-manager) and download and install Wicd.  

Get it from here:  [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

You can always re-install network-manager if you don't like it.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

Thank you! wicd did the trick for me. Oddly engough, when I first installed Gutsy as a beta, I was able to connect to the router with WEP enabled using my hex key. I only had problems when I recently did a fresh install. Then network manager never gave me the option to connect when I pasted my hex key. That button always remained inactive.

Figured out the problem with WEP and netmanager (for me at least). Copying and pasting the hexidecimel key from gedit was inserting a hidden character. Typing the whole number in by hand worked. Tried this when wicd didn't work so well after rebooting.

---

