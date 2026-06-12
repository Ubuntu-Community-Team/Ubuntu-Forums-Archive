---
title: "Could these deleting these files or quarnatining them cause problems?"
date: 2015-10-29
forum: General Help
---

### Post by michael-piziak on 2015-10-29
This is about files/folders that ClamTK detects and one chooses to delete or quarantine.

Most of these files are from Browsers (cahce I believe).

After quarantining files/folders, I noticed my system slowing down considerably, and screen greying out often.  Is this just a coincidence.

I also had a police scanner, I think Java heavy or Java script, running at same time - could have been it - ?

Rebooted and all is fine, but another thing is this:  If I run ClamTK and it finds a like 6 files, and I quarantine them, then I just rebooted and ran it again, and it like finds another handful of files - it's like the browsers are continuously picking up files that the ClamTK does not like.

But again to the question, could erasing these files or quarantining them cause problems?  Or would browsers just rebuild the files if needed.

See screenshot below of sample of files/folders:

p.s. Is there a limit to # of screenshot files I can upload?

---

### Post by yetimon_64 on 2015-10-29
Regarding your results, they are all PUAs (possibly unwanted applications). In [[COLOR=#0000ff]--this post--[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2295431&p=13358603#post13358603") I have posted a quote from the clamAV website advising users not to enable that test because of the posibility of false positives.

I will repost the quote here for your consideration.
> At this point we DO NOT recommend using it in production environments, because the detection may be too agressive and lead to false positives. In one of the next releases we will provide additional features for fine-tuning allowing better adjustments to different setups. **NOTE: A detection as PUA does NOT tell if a application is good or bad**. All it says is, that a file MAYBE unwanted or MAYBE could compromise your system security and it MAYBE a good idea to check it twice. I have added the bolding above to highlight probably the more important aspect for you to consider. 

Generally speaking, there are no viruses known to affect Linux "In the wild". I suspect your results would be a far bigger worry on a Windows system. All of those results shown are from the browser caches and should be safe to delete etc. I believe no action is being taken as they are most likely windows only exploits (not 100% sure on that, but on an Ubuntu only install I personally wouldn't be too concerned about them, but WOULD delete them being in the browser cache.)  

Just be aware if ClamAV/ClamTK etc ever detects your mime.cache (or any other system file) as a PUA, don't automatically delete them but check them out thoroughly; as seen in the post/thread I linked to above doing so can cause problems that may need repairing. 

Regards, Yeti.

---

### Post by Geoffrey_Arndt on 2015-10-29
Recommend two things:

1.    Avoid certain disreputable websites (porn of any type, get-rich quick, fix my windows, magic elixer, make my mojo bigger sites . . . you get the drift).
2.   Just uninstall Clam AV . . . really not needed especially if do no. 1 above)

---

### Post by michael-piziak on 2015-10-29
> **Geoffrey_Arndt said:**
> Recommend two things:

1.    Avoid certain disreputable websites (porn of any type, get-rich quick, fix my windows, magic elixer, make my mojo bigger sites . . . you get the drift).
2.   Just uninstall Clam AV . . . really not needed especially if do no. 1 above)

But I simply can't stop doing one of your 2 suggestions - big smiles.

Thanks for your intelligent reply though!

I look into turning that one thing off in Clam as the other poster suggested.

> **yetimon_64 said:**
> Regarding your results, they are all PUAs (possibly unwanted applications). In [[COLOR=#0000ff]--this post--[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2295431&p=13358603#post13358603") I have posted a quote from the clamAV website advising users not to enable that test because of the posibility of false positives.

Regards, Yeti.

ok, I want to turn Clam off from looking for PUAs, how do I do this?  

Below screenshot is my only options I can see in Clam preferences:

---

### Post by yetimon_64 on 2015-10-29
Can you show the next tab please (I don't actually use clamAV)? I think, if the setting is there, it may be on the next tab "Startup Preferences".

---

### Post by michael-piziak on 2015-10-29
> **yetimon_64 said:**
> Can you show the next tab please (I don't actually use clamAV)? I think, if the setting is there, it may be on the next tab "Startup Preferences".

Next tab screen shot below:

I have concluded that the problems with my system today, and all day today, is because of some Script problem.

Please see my post and video I show you at this new post I made:

[http://ubuntuforums.org/showthread.php?t=2301003](http://ubuntuforums.org/showthread.php?t=2301003)

Moderator - I'm hesitant to mark this thread as solved, but the problem is not caused by this thread, so perhaps you can just close this thread?

---

### Post by yetimon_64 on 2015-10-30
I can't see any option to turn that off. If you leave the thread open 'till another user who actually uses clamTK pops in you may at least learn if it is possible to do. 
In the mean time I'll have a quick check around to see if I can find any more info.
**Edit:** to turn off the PUA checks,
> The "Enable extra scan settings" option enables the ability
       to scan for PUA's, or Potentially Unwanted Applications as well as
       broken executables.

[COLOR=#0000FF][Source]("http://clamtk.sourceforge.net/README")[/COLOR]. (scroll down to section 6b, "Running clamTK")

---

