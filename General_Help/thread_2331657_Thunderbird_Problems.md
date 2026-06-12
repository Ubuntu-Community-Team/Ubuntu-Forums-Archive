---
title: "Thunderbird Problems"
date: 2016-07-24
forum: General Help
---

### Post by MarthaMyDear on 2016-07-24
Forgive me if I am posting this in the wrong forum...not really sure where it should go.

I originally changed my laptop to LUBUNTU a couple years ago and it worked GREAT! Light weight, fast...really a good
OS. Little by little I succumbed to "update" nags and now apparently have ended up with UBUNTU 16.04 LTS distribution in the LXDE desktop environment and the kernel is LINUX 4.4.0-31-generic (i686). I am using Thunderbird version 38.8.0.
My laptop is an old HP Compaq nc6220 1.73 gHz

I also have been using Thunderbird for a couple years and it worked flawlessly. In the last week it either become corrupted or something has changed. I have been able to move my emails within it to new folders so I am now able to send and receive HOWEVER Thunderbird displays an annoying trait in that when I click to launch it, it waits about 10 seconds before the little animated icon appears and starts moving to indicate messages are being downloaded.

I concede a lot of this is Greek to me so if I sound as if I am stupid, I am.

I checked my "Error Console" on Thunderbird and it shows the following 3 items:

```
While registering XPCOM module file:///usr/lib/thunderbird/components/libdbusservice.so, trying to re-register CID '{75a500a2-0030-40f7-86f8-63f225b940ae}' already registered by <static module>.

Failed to load native module at path '/usr/lib/thunderbird/components/libxpcomsample.so': (80004005) /usr/lib/thunderbird/components/libxpcomsample.so: cannot open shared object file: No such file or directory

Could not read chrome manifest 'file:///usr/lib/thunderbird/extensions/%7B972ce4c6-7e08-4474-a285-3208198ce6fd%7D/chrome.manifest'.
```

I suspect this might have something to do with my Thunderbird problems. As per the Thunderbird FAQ page I have already disabled the Lightning calendar which apparently is known to slow the email program.

Can anyone guide me as to how to correct these problems?

Any help is most appreciated.

---

### Post by wildmanne39 on 2016-07-24
*Thread moved to **General Help**.*

---

### Post by &amp;KyT$0P# on 2016-07-24
What version of Thunderbird are you running now, after the system update? (Are you sure it's still 38.8.0? [http://packages.ubuntu.com/xenial-updates/thunderbird]("http://packages.ubuntu.com/xenial-updates/thunderbird"))

Does the issue happen if you start Thunderbird in [Safe Mode]("http://kb.mozillazine.org/Safe_Mode")?

---

### Post by MarthaMyDear on 2016-07-25
Thanks for the reply Halogen2. Am I sure that I am running Thunderbird 38.8.0? That is what comes up when I select the "HELP" tab on Thunderbird and then click "About Thunderbird." How else can I verify the version?
Yes, it also happens when I start Thunderbird in SAFE MODE.

Also I am noticing new sluggishness on Mozilla Firefox as well...but the effect to Thunderbird is far more pronounced.

---

### Post by &amp;KyT$0P# on 2016-07-25
So the first thing to do is get a Thunderbird version that's compatible with Ubuntu 16.04.  Can you upgrade to Thunderbird 45.2.0?
(completely quit Thunderbird, then run: )
```
sudo apt-get update
sudo apt-get --reinstall install thunderbird
```

Since you use Lightning, you would then need to update that as well.  Lightning contains binary component(s), so each version of Lightning is only compatible with one single version of Thunderbird.

Does that fix the problem?

> How else can I verify the version?
Since you installed the Ubuntu package manager Thunderbird, running this in a Terminal will work:
```
dpkg-query -W | grep -F -i 'thunderbird'
```

---

### Post by MarthaMyDear on 2016-07-25
No, I'm afraid that didn't solve the problem. Thunderbird still hesitates before polling my email accounts
about 20 to 25 seconds.

I did check the version of T-bird and here's what came up:

    1:45.2.0+build1-0ubuntu0.16.04.1

Checked my Thunderbird "Error Console" tonight and here's what came up (3 items):

Could not read chrome manifest 'file:///usr/lib/thunderbird/chrome.manifest'.

Could not read chrome manifest 'jar:file:///usr/lib/thunderbird/extensions/%7B972ce4c6-7e08-4474-a285-3208198ce6fd%7D.xpi!/chrome.manifest'.

While creating services from category 'profile-after-change', service for entry 'SpeechDispatcher Speech Synth', contract ID '@mozilla.org/synthspeechdispatcher;1' does not implement nsIObserver.

Not sure what any of it means but perhaps it is significant to someone with a trained eye. 

Appreciate your help.

---

### Post by &amp;KyT$0P# on 2016-07-25
Sorry but the forum software is not currently letting me post all of my next set of suggestions, and I need to include too many links to reasonable just post a screenshot of the text.  So I only post one now, I'll try to post the rest later.

In case the delay is due to message folders being really large, try this:
1) Completely quit Thunderbird
2) **Important: Back up your entire [profile folder]("http://kb.mozillazine.org/Profile")**
3) Re-open Thunderbird, then (after the delay) manually [compact all your Thunderbird folders]("http://kb.mozillazine.org/Compacting_folders")

And if that doesn't help... then I'd probably go through [**copying** data to a new profile]("http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Thunderbird") step by step, checking for the problem after each step, and see if/where the problem returns.

However, if any of your email accounts are set up as POP, there is a risk of losing messages that arrive during that procedure.  Does the delay occur if you disconnect from the Internet before starting Thunderbird?  If so, for this reason I would recommend disconnecting from the Internet while working with a secondary, diagnostic profile.

Anyway, if the problem returns after copying prefs.js... well, I know how to troubleshoot it but I don't know any simple or safe way of troubleshooting it :mrgreen:
So, if that is the case, it is probably safest to disconnect from the Internet, create a new [profile]("http://kb.mozillazine.org/Profile"), set up your email accounts **in exactly the same order you set them up in before**, then migrate all your settings and data **except for prefs.js** into the new profile.
If the problem is still gone, then try manually reconfiguring Thunderbird and your extensions, and checking again.  If still gone after that, then the previous profile was probably corrupt.  Problem solved.

Some things for you to work with in getting rid of the problem, hope it helps.

---

### Post by MarthaMyDear on 2016-07-26
Halogen...

Really, really, really appreciate your willingness to help. I am going to try your suggestions in your
last posting and will report back.

Thanks so much.

---

### Post by DuckHook on 2016-07-26
> **MarthaMyDear said:**
> My laptop is an old HP Compaq nc6220 1.73 gHzWhile all of halogen2's suggestions are definitely worth trying, it is also possible that your laptop is running up against its limits. The specs for this machine are quite low by today's standards, which is probably why you installed Lubuntu on it (good thinking doing so, btw :KS ). Please post any info you have about its specs. The default specs say 1 GB RAM which could quickly throw memory access into SWAP, especially if your email database is large. This would slow your system down a lot. The next time T-Bird is up and running, open a terminal and please post back the results of:```
free -h
```

The following procedure is also very instructive: before launching T-Bird, open a terminal and run:```
top
```...then open T-Bird and note where and how much difference there is in %CPU and %MEM allocation for the various processes running on your system. *htop* has a nicer interface, but you have to install it first.

---

### Post by MarthaMyDear on 2016-07-31
While I concede my laptop is older I do not believe this is causing my problem. My problem started when I foolishly did one of either of two things: 1) Got sucked in to the hype about booking a hotel online through hotels.com AND/OR 2) Checking into the hotel 8 hours later and using their wi-fi to retrieve my emails. From that point on I could not retrieve emails on any of my accounts through Thunderbird and Thunderbird itself began acting screwy. I have since been able to massage Thunderbird to where it retrieves and sends emails from my accounts but the remaining issue is the odd behavior when I click to launch Thunderbird to "GET ALL MESSAGES." From the instant I click GET ALL MESSAGES it takes 12  to 15 seconds for the little moving bar to appear to indicate that my accounts are being poled. THIS IS A NEW ANOMALY. Prior to hotels.com AND/OR the hotel's wi-fi when I clicked GET ALL MESSAGES, the moving bar appeared immediately and began polling my accounts.
That remains my only issue.
I have removed and re-installed Thunderbird and it picked up the emails in my PROFILE perfectly. But I know things are not right yet.

---

### Post by &amp;KyT$0P# on 2016-07-31
> **MarthaMyDear said:**
> My problem started when I foolishly did one of either of two things: 1) Got sucked in to the hype about booking a hotel online through hotels.com AND/OR 2) Checking into the hotel 8 hours later and using their wi-fi to retrieve my emails. From that point on I could not retrieve emails on any of my accounts through Thunderbird and Thunderbird itself began acting screwy. 
:o Now this is sounding to me like you could be dealing with the symptoms of malware infection.  If that is indeed the case - which I am not sure if it is or not - then you will need to take drastic measures of some sort to be sure to get rid of the malware, and more measures to prevent similar incidences from happening again.

So the first thing to do now is, double-check your add-ons list.
Do you recognize everything listed there?
Malicious add-on might hide itself from add-ons manager, so does your profile folder contain any additional add-ons in the extensions/ sub-folder?

I'm a total newbie in dealing with malware infections on Linux, so I can't reasonably suggest anything further until someone better versed in that gives their take on the situation.  Also, it's now unclear if there is currently any point trying the profile tests and such I suggested earlier, because malware can persist through all that.

---

### Post by MarthaMyDear on 2016-08-01
Thanks again, Halogen...I think you're guiding me in the right direction.

I guess I subconsciously rule out the presence of the obvious...viruses and malware...because of the
hype about Ubuntu/Linux not needing antivirus protection. But clearly something happened and this morning
I am more convinced than ever that I picked something up.

After a quick scan of this forum I thought I would install CLAMTK to see if it finds anything. I went to my "Lubuntu
Software Center," typed in ClamTK and it came up in the window. I added it to the "apps basket." But the installation
tab remains "greyed-out" and I am unable to install it. H-m-m-m. Something fishy here.

I am hesitant to download it from the numerous Internet sites because I suspect many of them are really inducing
malware themselves.

By the way, I did check my add-ons list and there were a couple that I didn't recognize (which in itself doesn't mean anything)...
"NoScript", "Disable DHE" and "Ubuntu Modifications" ---so I disabled all of my add ons but there was no change.

I would welcome any suggestions and wonder what you think about BleachBit although the warning about it on this
forum are of some concern that it will wipe out TOO much.

---

### Post by &amp;KyT$0P# on 2016-08-01
> hype about Ubuntu/Linux not needing antivirus protection
Linux **does** need antivirus.  What it doesn't need is a constantly-running realtime AV program.
I've found that intelligent use of an antivirus *scanner* such as ClamAV (which ClamTK is a front-end) is a useful layer of protection.  Good for you figuring that out. :)

The software center type programs for 16.04 are known to be buggy.  Try installing ClamTK from the command line.
```
sudo apt-get update
sudo apt-get install clamtk
```

> By the way, I did check my add-ons list and there were a couple that I didn't recognize (which in itself doesn't mean anything)...
"NoScript", "Disable DHE" and "Ubuntu Modifications" ---so I disabled all of my add ons but there was no change.
I'm not sure what to make of that either.  NoScript is the name of a [legitimate add-on]("https://noscript.net/"), but it is not compatible with Thunderbird and I didn't think it was possible to install it in Thunderbird. :-k

Don't know anything about the other two.

> I would welcome any suggestions and wonder what you think about BleachBit although the warning about it on this
forum are of some concern that it will wipe out TOO much.
I would NEVER use an automatic cleaning type program on Linux.  Ever.  Those programs, if set loose on Firefox profile or Thunderbird profile, usually screw it up beyond repair.

Then again, I generally assume that a Linux system takes care of itself - and when it doesn't seem to, backup + manual cleanup is safest.

That's just my opinion for what it's worth.  Again, I have no experience with infected Linux systems...

---

### Post by DuckHook on 2016-08-01
> **MarthaMyDear said:**
> …I subconsciously rule out the presence of the obvious...viruses and malware...because of the
hype about Ubuntu/Linux not needing antivirus protection. But clearly something happened and this morning
I am more convinced than ever that I picked something up.
> **halogen2 said:**
> Linux **does** need antivirus.
Please don't spread such erroneous conceptions. There are no known Linux viruses at large in the wild. AV programs like ClamTK exist to find Windows viruses. Unless you are running WINE, Windows viruses do not infect Linux.

Worms and Trojans are a different matter. They *will* infect Linux machines but the user must actively do something really foolish to allow this… usually involving the installation of an app from outside the repositories, or running sudo on an untrusted link, or surfing as the root user, or taking risks of similar magnitude and silliness.

In any case, AV apps are useless and a waste of time on a pure Linux box. Some users justify its use because they don't want to pass Windows viruses on to their Windows-using friends. In my opinion, this is just enablement behaviour, but to each his own. A legitimate use (the only one I can think of) is for those running a mail server and wanting to filter out all Windows viruses. But I doubt that OP is running a mail server, so this reasoning doesn't apply.

I've written an extensive post about this in an old thread. There's no point in repeating it yet again, so here is the link, in case you are interested:
[https://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795](https://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795)

> **MarthaMyDear said:**
> I would welcome any suggestions and wonder what you think about BleachBit although the warning about it on this
forum are of some concern that it will wipe out TOO much.@OP Long-term posters to this forum will tell you that there are few users more paranoid than me. So, I'm not about to dismiss your concerns. Although there is a good chance that your problem is not due to malware but rather, to too large a cache or a corrupted config file, in the murky world of security, it is impossible to rule out malware. So, here's what I suggest:

Whenever anyone is worried about a compromised system, there is no point in trying to "clean" it or "fix" it. The only procedure guaranteed to work, and&#8213;just as importantly&#8213;to put your mind at ease, is to back up your data, nuke the current install, start over with a known good install and restore your data.

After you get back to a good install and have restored the data that you need, follow the guidelines in my link. Learn about apparmor and start using it. Review your logs as an ongoing habit, especially auth.log, syslog and dmesg. Implement each and every one of the items in my link. Most of all, get into the habit of treating security as a *user* process of learning, vigilance, and good habits, rather than installing some magic app. You will note that nowhere in my suggestions do I include installing AV apps.

For even more info on Ubuntu security, I encourage you to read the link in my sig: ***Security Basics***

---

### Post by kurt18947 on 2016-08-01
Here's something that's pretty simple to try. Start Thunderbird from terminal with 

```
thunderbird -p
```

This will open a windows allowing you to create, edit or delete profiles. You could create another profile and use that for a bit. If it helps move your messages but not settings from the old profile to the new. Sometimes hotel guest internet services trying to be clever - aren't.

---

### Post by MarthaMyDear on 2016-08-02
Kurt,

That did it! Thank you!

I followed your advice and created a new profile for Thunderbird as well as a new profile for
Firefox and now my Thunderbird works as it did before...fast and flawlessly. The new profile
also improved the performance of my Firefox as well. Now it's just a metter of figuring out
how to copy BOOKMARKS in Firefox and copying my emails from the old Thunderbird profile.
Hopefully there isn't a worm or virus remaining that I will copy with them.

Halogen...thank you for your advice too. I was able to install CLAM and snooped around but it did
not find any viruses. Unfortunately it seems to e file-specific instead of doing a full hard drive scan so I
could have missed something. More troubling is the possibility that a worm has infected my computer which,
evidently, CLAM does not see.

Thanks to you both. You have have so helpful and I am grateful.

---

### Post by SeijiSensei on 2016-08-02
If you use IMAP, your mail should be in the old .thunderbird directory in its ImapMail directory.  You could try copying that whole directory over to the new profile and see if it works.

---

### Post by &amp;KyT$0P# on 2016-08-02
You're welcome! :KS

The fact that a new profile fixes it means your computer is very unlikely to be infected.  Thunderbird doesn't run as root.

As for transferring your settings and data, that's explained in the links I posted earlier - [https://ubuntuforums.org/showthread.php?t=2331657&p=13522600&viewfull=1#post13522600](https://ubuntuforums.org/showthread.php?t=2331657&p=13522600&viewfull=1#post13522600)
You will **not** copy a worm or other Thunderbird-specific malware infection if you do not copy your extensions.  If you're concerned about that - completely quit Thunderbird, back up all your profiles, then:
1) switch back to your old (broken) profile
2) delete - but do not read - all spam & the like (if any)
3) compact all your folders
4) switch back to the new profile
5) manually re-download and reinstall all your extensions from [https://addons.mozilla.org/](https://addons.mozilla.org/)
6) transfer all other desired data and settings, and hope the problem does not return

---

### Post by DuckHook on 2016-08-02
> **MarthaMyDear said:**
> More troubling is the possibility that a worm has infected my computer which,
evidently, CLAM does not see.I think it is important for you to understand how worms work so that you can escape from underneath this general sense of dread that you seem to be labouring under. Without dismissing the gravity of the damage that worms can do, they are nonetheless an overstated risk for the average user. By their very nature, they can exist only if they can propagate. If they cannot propagate, then your chances of having one are next to zero. And they propagate mainly by exploiting specific security holes in the OS. If those security holes are closed off (patched), then there is no point of entry available to them and they are, for all intents and purposes, harmless to the *patched* system. You probably see where I'm going here: the key to squashing worms is not AV, but keeping your OS properly patched and updated. Linux is pretty good at patching serious security holes and Ubuntu likewise. So long as you update/upgrade your system conscientiously, worms should not be a concern.

In your case, since a new profile brought your system back to its old level of responsiveness, you should put further thoughts of worms, Trojans, rootkits and other malware into their proper place (as simply long-term security concerns that should be addressed through good security practices I've already pointed you towards) and not let it govern your current situation nor allow it to define your next immediate steps.

---

### Post by MarthaMyDear on 2016-08-04
Duck Hook and Halogen2...really appreciate your help.

It looks like I've got Thunderbird running normally now and the only issue that remains
is trying to retrive my email messages and put them back into my new profile. Evidently
in all of my kludging to try to get this thing to work I replaced my emails in the old profile
with only a handful that had arrived and were in the new profile. HOWEVER I still have the POP3
files that are located on the Hotmail website that contain all of my original emails. 

Do you or anyone here know how I might be able to import the emails ON THE HOTMAIL WEBSITE
and either display them in my Thunrderbird iinbox or in a local folder within Thunderbird?

I know I should have set this thing up using IMAP but, years ago when I did I did not realize the
difference between IMAP and POP3; so I have to play the hand with the cards I am dealt.

---

### Post by &amp;KyT$0P# on 2016-08-04
If all you want to transfer is mail:
1) Create folders in Local Folders corresponding to the folders you have for your hotmail
2) Move all messages to said folders in Local Folders
3) Completely quit Thunderbird
4) Replace the entire Mail/yourhotmaildomain folder with that from your old profile
5) Start Thunderbird again and check that the messages you want are there.  If so, move the messages back out of Local Folders to where you want them.

By the way, switching to IMAP is possible, but that's for another thread.

---

### Post by kurt18947 on 2016-08-05
> HOWEVER I still have the POP3
files that are located on the Hotmail website that contain all of my original emails. 


I'm not near a Thunderbird install right now. You want to change a default account setting to save POP3 email on the server. The default setting is to save emails for 14 days. I change that to 'save emails until I delete them' or words to that effect. I *think* that's in Account Settings but I'm not certain.

Edit: Yup, Email account -> Server Settings -> Server Settings.

---

