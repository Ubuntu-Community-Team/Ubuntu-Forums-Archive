---
title: "[SOLVED] Firestarter multiple connection configuration"
date: 2007-08-12
forum: General Help
---

### Post by gobbles414 on 2007-08-12
Hi all,

I have a laptop with both wireless a/b/g and ethernet hardware installed. My job is starting to take me on the road more often. Of course, this means that sometimes I will be using wireless and other times ethernet. **Is there a way to tell Firestarter to protect both connections automatically?** Then, I won't have to run the wizard when I switch from wireless to ethernet or visa versa.

P.S. This question has been asked by several users in the forums. But I cannot find any who have gotten a response. Here is an [example]("http://ubuntuforums.org/showthread.php?p=2924522").

---

### Post by gobbles414 on 2007-08-12
bump

---

### Post by porcorosso on 2007-08-12
I'm interested in various aspects of Firestarter, too. I'm sorry I don't know the answer to your question.

I don't know if you've located the manual at [http://www.fs-security.com/docs.php#docsdownload]("http://www.fs-security.com/docs.php#docsdownload")

I went through it briefly just now and found no specific mention of your issue, though I could certainly have missed it.

I hope you get an answer.

---

### Post by euler_fan on 2007-08-12
As a fellow laptop user I have never noticed a problem going from wired to wireless and back.

AFAIK, when using Firestarter it sets up one set of firewall rules that get applied no matter how you connect to the Internet.

You feel you need more aggressive monitoring you can have Firestarter minimize to your tray. When I have done this and gone back and forth between connection types, nothing happens.

Another thing to try in order to test things is to use Shields Up! before and after switching. If anything changes, then you firewall has changed.

All in all, unless you hear from someone with more knowledge than I have I don't know of any reason to be at all concerned.

In addition, it is commonly said that on a properly patched Ubuntu box not running any services (like apache, SSL, remote desktop, etc) then there is little or no need to set up your firewall, AV, or IDS/IPS. I personally disagree, but it the whole question of personal computer security in a linux environment is a pretty controversial topic around here. I use firestarter, OSSEC-HIDS, ClamAV, rkhunter, and chkrootkit regularly myself.

There is a good link [here]("http://ubuntuforums.org/showthread.php?t=510812") which discusses security on a desktop Ubuntu environment.

If you have a corporate laptop I would also check with your IT folks about what they want you to have.

I HIGHLY recommend making a full backup before going on the road and using TrueCrypt to secure any sensitive information as well as KeePassX to store all you passwords and keep a copy of your password file on a USB key in your pocket and a spare somewhere in case it gets lost and your lappy stolen. Between those two precautions even if your machine is stolen you should still be able to basically pick up where you left off knowing your sensitive information is mostly protected. It will at the least buy you some time while you change everything. [Dark Reading]("http://www.darkreading.com/") has an article about laptops being stolen and how to prepare for and handle that. It is entitled, aptly, [Assume your laptop will be stolen]("http://www.darkreading.com/document.asp?doc_id=131100"). There is a nice gui for TrueCrypt [here]("http://bockcay.de/forcefield") called Forcefield for Feisty.

---

### Post by euler_fan on 2007-08-12
[Look here . . . ]("http://www.fs-security.com/docs/persistence.php")

Unless you are using dial-up or installed from source (e.g. you are an ethernet/wifi user who installed from synaptic or an equivilent system) you will be fine as the firewall is always running.

Everything else I said before is still true though.

Oh, and if you keep copies of critical files on a USB key, I would suggest leaving it in your pocket or sticking it into your sock (assuming you're a man and wearing slacks . . . ) or someplace else NOT with your laptop case, briefcase, wallet, or keys. A mugger is more likely to take your whole laptop bag and ignore the possibility of a USB key you have stuck someplace on your person which is not obvious than to take the time to pat you down to get every last item off of you.

Unless they know you are someone who carries sensitive data on a USB Key, in which case [ you might want one of these]("http://www.pcstats.com/artvnl.cfm?articleID=1913") if it works with Ubuntu or else put a TrueCrypt partition on your flash drive. With recent news items about doctors carrying around patient data on unencrypted personal flash drives, if you carry any sensitive data I would highly suggest it--especially if you look the part of someone who might have important information on your USB key. Some robber might just have read it and think they can either (a) embarrass you or your company or (b) profit personally from the information.

Now that I have you mildly paranoid, have a good trip :)

---

### Post by ruibernardo on 2007-08-12
Firestarter is easy and popular but to be like this it is very rigid in some ways. One of them is the number of network interfaces it manages and the way to change between them. 

If you do have 2 (or more) interfaces to connect to the internet, running the Firestarter Wizard is the only way to guarantee that the firewall is active for that interface. That's because when you run the Wizard and change the interface, Firestarter will adapt the iptables to the new interface and to its configuration (DHCP, gateway, etc).

A configuration for one interface may not be the same of the other. Changing between Wireless and an other interface will break the iptables script. You have to run the Firestarter Wizard each time you change the interface.

It's easy to check this. Run the wizard for one interface, change the interface you are using to connect to the other interface and make a "sudo iptables-save". You will find that iptables is still referring to the first interface. Try a "security scan" from grc website, and it is very likely that the results will not be what you expect. Again, run the "Wizard", update it to the actual and active interface, check "sudo iptables-save" and grc website and the results will be different.

From the mailing list of Firestarter, there is [suggested "workaround" to make this "automatic"]("http://sourceforge.net/mailarchive/message.php?msg_id=Pine.LNX.4.64.0601180458001.8863%40lai.local.lan"). I do not have wireless, nor two interfaces, so I can't help, but take a look to what it's suggested for this problem. 

You may consider less GUI "firewalls" to not have this kind of problems.

Hope to have helped is some way.

---

### Post by euler_fan on 2007-08-12
@epimeteo 

FYI: The link to the workaround (which I am interested in implementing myself . . . ) just points to the Ubuntu forums reply page.

---

### Post by euler_fan on 2007-08-12
[Is this the link you meant?]("http://sourceforge.net/mailarchive/message.php?msg_id=Pine.LNX.4.64.0601180458001.8863%40lai.local.lan")

---

### Post by ruibernardo on 2007-08-12
Opss, sorry about that. Yes it is :)

---

### Post by euler_fan on 2007-08-12
Incidentally, I asked this question today of the Firestarter mailing list and will post their responses here when I get them.

EDIT: P.S: I don't know any bash, otherwise I would write such a script myself and post it.

EDIT: P.P.S: When I get back to somewhere where I have both a wired and wireless connection I'm going to do some testing to see if the issue is still current myself as well. Will post results. I do hope this issue does away in some future version . . . fwbuilder seems like a great but overkill tool for solving this problem.

---

### Post by gobbles414 on 2007-08-12
Hi all,

Thanks for posting responses to my question. I'll take a look at the information tonight and post again by Monday evening.

---

### Post by gobbles414 on 2007-08-13
Hi all,

Well there are a lot of suggestions that are worth a reply; so I'll try to address all of them.

I may look into the data encryption idea at a later time. There have been some good issues raised on that front. Luckily, I carry very little sensitive data on my computer at the moment. That will probably change at some point in the future. I'll do some more investigating soon.

OSSEC-HIDS seems like a great program. I may try it out later but it is very likely overkill for my needs. I use Avast instead of ClamAV. But the main thing is that we agree that an antivirus program is a good thing to have. Rkhunter has worked fine for me. But chkrootkit closes the terminal window as soon as it finishes the scan, unless I do the scan in expert mode.

**One of the links provided in this thread led me to discover a program called lokkit.** Although I still have some testing to finish, I think that it will eventually replace Firestarter on my system. The interface for lokkit is several years old, and the software itself seems to be a port of a Red Hat app. Also, it seems to close all of the ports on my computer in normal mode. It works better, apparently, in -f mode. _What I really like is that it gives the user the option of managing multiple network interfaces!_ **However, I cannot find an option to control stealth mode or ICMP filtering.** I obviously still have some investigating to do.

---

### Post by euler_fan on 2007-08-13
The only thing about OSSEC-HIDS is that installing from source I don't think the init.d script works. When I use htop to check on it after a reboot none of its components are running like they are after I manually start it (but there are hooks to make it run at startup . . . )

Then again, if you routinely start conky (for instance), also starting OSSEC-HIDS is not a big deal. I may just create a custom script to autostart them both on startup unless someone can tell me what's going on with the original OSSEC init.d script.

---

### Post by gobbles414 on 2007-08-14
Hey euler_fan,

If/When I ever get around to trying OSSEC-HIDS, I'll keep that in mind.

---

### Post by euler_fan on 2007-08-14
> **gobbles414 said:**
> Hey euler_fan,

If/When I ever get around to trying OSSEC-HIDS, I'll keep that in mind.

I figured it out. The init.d script works great if your machine automatically connects to the network at startup.

If, however, you have the SSID for your wireless network hidden or otherwise have to manually connect then OSSEC-HIDS won't start and has to be started manually.

Now i just wish I knew enough bash to start/restart OSSEC-HIDS on connecting. :)

---

### Post by gobbles414 on 2007-08-27
I've switched to the NON-Gnome version of Lokkit. The Gnome version crashes in Feisty.

---

