---
title: "Proper way to update/patch Ubuntu and also... Whither Firefox 59.x?"
date: 2018-02-06
forum: General Help
---

### Post by Ronald_F._Guilmett on 2018-02-06
I confess to being a mostly naive Ubuntu user.  I've been using it for some time, but not often.  I'm far more familiar with other (non-Linux) systems, but I've been using Linux/Ubuntu more and more lately.

So, here are my naive questions for today:

(*)  Is there a document someplace I should read on the tropic of how to properly maintain an Ubuntu desktop system?  (I'm running 16.04 LTS, BTW.)

In the past I tried to update everything using the GUI-based Ubuntu Software tool/thingy, but that appeared to me to crash and burn for some not very well explained reasons.  That's quite alright.  I am more comfortable doing things with the command line anyway.  And recently, I found a doc someplace online that said that the process was as simple as switching to root and then just doing;

apt update
apt upgrade

which I have now done.  (I also did "apt autoremove" because the output of one of the other two commands above suggested it.)

Anyway, I am guessing that maybe it would be Best if I set up some sort of cron job or something to do these two or three commands every day.  But perhaps there is more to maintaining a fully patched Ubuntu that just that.  If so, then I'd like to educate myself.  Links to relevant and/or helpful documents would be appreciated.

(*) No software is perfect, and I do suspect that it is not beyond the realm of possibility that one or more of the steps performed when "apt upgrade" is executed may perhaps fail... and perhaps even in a not-so-obvious way.  I saved the output of that command to file (using script) however because its subprocesses use all sorts of fancy schmany control sequences (e.g. to overwrite the current line, in different colors even) and also because I don't know how failures would even be exhibited in the plain-text parts of the "apt upgrade" output anyway, I don't think that I can just simply check that the updating process was FULLY successful just by grepping that file for the word "fail".  So how does one check to see that every single last blessed little thing that was supposed to have been done by "apt update" really did get done successfully?

(*) Press reports indicate that various patches have been released to either cure or mitigate the Meltdown and Spectre hardware bugs.  How can I check whether or not my specific instance of Ubuntu 16.04 LTS has or has not already had all relevant and available patches applied for these specific very serious security problems/issues.

(*) Are patches currently available, and will they be installed via a successful "apt update; apt upgrade", for the Meltdown issue?  Same question also for the various Spectre sub-issues (which are now numbered, I believe).

(*) On January 30th, 2018, TheRegister reported on a "critical" security flaw affecting Firefox versions 56.x, 57.x, and 58.x and suggested that user should immediately update to Firefox 59.x.  Earlier today, I again did "apt update; apt upgrade" in the hopes that this would bring me up-to-the-minute, as least as far as "critical" security issues were concerned.  I then re-ran my installed Firefox which reported (via its "About" link) that it was still stuck at 58.0.1.  So, um, what gives here?  What did I do wrong?  And more to the point, how do I fix it?

Using the words "critical" and "security" in the same sentence, along with the name of any software or hardware tool that I use on a regular basis is more than enough to get my attention.  My attention is now focused on my Ubuntu system, the instance of Firefox currently installed thereon, and also the Meltdown and Spectre patches... the ones that may or may not be available and the ones that may or may not be present and successfully applied on my specific system.

Thanks in advance for any responses.

---

### Post by TheFu on 2018-02-06
That's a bunch of questions.  I don't know all the answers, but  .... [https://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](https://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

Just replace apt-get with **apt**. apt is preferred.

I wouldn't patch daily.  New is the enemy of stable, so modifying they system daily seems obsessive. Weekly is when I do it.

Ubuntu security patches are complicated. They might be back ported to the version already on the system where the 3rd number in the version of x.y.z - z would be incremented.  'z' level changes are only for bug fixes that don't change behavior or APIs.  

For the CPU issues - there have been many patches released and conflicting recommendations from the different vendors involved.  Trust that Canonical is doing what is best. You can google for answers on how to see if your system has or hasn't been patched.  I've seen threads in these forums about that as well.

As for failures in Unix-like systems, there is an expectation that when things work, nothing is said.  When things fail, complain loudly.  This is part of the [Unix philosophy]("https://en.wikipedia.org/wiki/Unix_philosophy").  Is is worth keeping that in mind when working on a Linux system. There are other important ideas in there too. 

That's all I got. Sorry.

---

### Post by ian-weisser on 2018-02-06
> **Ronald_F._Guilmett said:**
> maybe it would be Best if I set up some sort of cron job or something to do these two or three commands every day.

Already done for you. Check your 'Software & Updates' control panel, and ensure that Security Upgrade are set to install automatically.
Non-security upgrades are rather optional. If you want them, you can 'sudo apt upgrade' to install those whenever you like. Weekly, monthly, or never.

> **Ronald_F._Guilmett said:**
> perhaps there is more to maintaining a fully patched Ubuntu that just that.

Mark your calendar for mid-2018, and then run 'do-release-upgrade' to migrate from 16.04 LTS to 18.04 LTS.
Unless you have a problem, that's about all you need to do.

> **Ronald_F._Guilmett said:**
> how does one check to see that every single last blessed little thing that was supposed to have been done by "apt update" really did get done successfully?

Look for the word ERROR in the four-or-so summary lines at the end of the output.

> **Ronald_F._Guilmett said:**
> How can I check whether or not my specific instance of Ubuntu 16.04 LTS has or has not already had all relevant and available patches applied for these specific very serious security problems/issues.

Easy Way: Ensure you have automatic security upgrades enabled.

Manual Way: Look up the relevant CVE at [http://security.ubuntu.com](http://security.ubuntu.com). That will tell you the new version number of each fixed package. Then run 'apt policy <packagename>' to see which version number is currently installed.

> **Ronald_F._Guilmett said:**
> Are patches currently available[...]for the Meltdown issue?  Same question also for the various Spectre sub-issues 

Visit security.ubuntu.com and see for yourself.


> **Ronald_F._Guilmett said:**
> "critical" security flaw affecting Firefox versions 56.x, 57.x, and 58.x and suggested that user should immediately update to Firefox 59.x.

That's ONE way, not the ONLY way, to address security vulnerabilities. Visit security.ubuntu.com to see how the Ubuntu Security Team handled this CVE, and pushed the fix out.

---

### Post by Ronald_F._Guilmett on 2018-02-06
Thank you TheFu, for at least taking a stab at answering my questions.

You didn't notice, but I actually ***am ***using apt , rather than apt-get.  (See the post that you were replying to.)

I guess that I will need to get down and grovel through these forums, and perhaps use Google, to try to find the answer to my simple questions about Meltdown & Spectre patches.  I do trust Canonical, but am a big believer in that old Russian saying that was made popular during the (President) Reagan, years, "Trust, but verify."  I do not outsource my security blindly, and would at least like to know the current state of play with respect to my specific system, and which relevant patches have or have not been applied.

And I have more than a little reason to suspect that my system is ***not ***currently patched up to protect me from these (CPU) issues, even though I have just today fetched and applied what I believe to be all currently released Canonical patches.

Which brings me to the main reason why I posted my set of questions, the most important of which you did not address at all:  Why is Canonical still only giving out Firefox 58.0.1?  It has been around eight days already since even the TheRegister knew that there were "critical" security flaws in that... flaws which are allegedly fixed in the 59.x.x release(s)... a Firefox release which has been generally and widely available already for at least the past 8+ days ?

If this is Canonical's idea of prompt distribution of updates/patches for critical security issues... well then they and I have rather different ideas about the meaning of the word "timely", and also, this makes me wonder if they are likewise sitting on a pile of unreleased Meltdown/Spectre patches as well, and not making ***those*** generally available yet.

I worry a lot.

With respect to your suggestion that if "apt upgrade" were to fail in even the slightest way (e.g. one component or one library failing to properly update) that the result would be a ***very ***noticeable failure, i'm afraid that I will have to question that assertion.  What makes you so sure that the thing would crash and burn if there was a failure in the update process for just one of the many diverse things which "apt upgrade" works to update?  Having looked at the output generated by "apt upgrade" I am not so sure that none of those messages imply that ***bad things ***have occurred during processing, e.g. of various install scripts.  (In and among the output I see ***many ***very obscure *warnings *and if even all of those are only for benign issues, I wonder why Canonical is so sloppy as to not eliminate those, i.e. in order to allay fears that something has gone awry.)

Lastly, while I thank you for your obviously well-meaning attempts to educate me regarding The UNIX Philosophy, I feel it is appropriate to note that I've been working on and with UNIX and UNIX-like systems since the early 1980s, both as an administrator and as a software engineer.

You probably mistook me for an ordinary end-luser noob due to my assertion that I'm not too awfully familiar with ubuntu, specifically.  But UNIX and I go way back.

 P.S.  I just now noticed that on this web site there is at least one security-specific forum.  I guess that I should repost some of my questions there.   Sorry.  My bad.  My mistake.  I should have started out there.

---

### Post by TheFu on 2018-02-07
I was a Unix admin for 20-ish years too.  We get all sorts of questions from people of varying backgrounds here. It is very difficult to guess at which level someone might be, but the vast majority are completely new to Unix-like OSes.

**APT vs apt-get**
I didn't mean to imply that you weren't using apt.  I was just pointing out that the linked article says to use apt-get and that "apt" is preferred now.  It didn't exist when that article was written.

**Firefox Update**
Also, I think you miss understood the meaning about how security patching might be handled in the Ubuntu LTS world.  Having the latest and greatest program for X isn't how those work by default.  I looked for the 59.x critical bug and didn't see any.  I did find a 58.0.1 bug fix, however.  [https://www.mozilla.org/en-US/firefox/58.0.1/releasenotes/](https://www.mozilla.org/en-US/firefox/58.0.1/releasenotes/)

**CPU bugs** - opinions follow
I'm like you, trust but verify.  However, there are too many unknowns here to provide an answer. Not all CPUs will get patched. Intel only supports CPUs less than 5 yrs old.  Whether they will/have made any firmware updates available for older CPUs is a different question.  Redhat determined a few weeks ago that the Intel updates were bricking many systems, so they removed it.  I'd already done my research on each of the issues by that point and decided for my risk levels that it simply didn't matter to me - patched or not.  I was curious and looked up how to check whether my systems were patched, ran the commands, and none were updated for the intel firmware at the time.  It was a hassle, since the CPU capabilities and a dodgy Intel program were necessary.  Intel has a habit of updating code but I'm never notified about it.  They expect the motherboard makers to provide updates ... not exactly a great support method outside the server lineups, if you ask me. 2 of my CPUs are able to be patched - one is a chromebook that hasn't run ChromeOS more than 30 minutes (no patches for it!) and the other is 4.5 yrs old Gigabyte motherboard, so I won't hold my breath for firmware updates that don't require Windows to apply.  I expect that Linux kernel updates will recognize patched and unpatched CPU firmware, BIOS firmware and take protective actions based on what is necessary across 1 yr old and 10 yr old hardware.  If I were in a business environment with high profile, constantly attacked, internet-facing servers, then I'd care much more.  I'd also have a support contract with Canonical in that situation and would have called them for the straight poop.  Canonical posted a new webpage last month that has been updated for how both CPU issues were being addressed.  [https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown) <--- I had to search for this.

**APT Failures**
What 1 person considers "noticeable" doesn't mean someone else will. I would expect a Unix admin would recognize a failure.  When I run apt, **any** issues are pretty clear and jump out (to me).  If you aren't seeing clean runs, there is an issue to be fixed. 

Which sub-forum to which any group of questions belongs is a judgment call.  It is often best to ask 1 question per new thread, unless they are related.  Different people will chime in on the different questions. Posting the same question in multiple sub-forums isn't allowed.  The moderators will usually move questions to a different forum as needed, usually going for the most specific group of volunteers for where they hang out.

I don't worry very much, but I do make action lists for things that need to be followed up. Until there is something I can actually do, worrying doesn't help me.  I haven't looked deeply for how other Linux distros are handling these issues the last week or so.  Are they *doing any better* since Linus called Intel's patches "complete and utter garbage?" [https://techcrunch.com/2018/01/22/linus-torvalds-declares-intel-fix-for-meltdown-spectre-complete-and-utter-garbage/](https://techcrunch.com/2018/01/22/linus-torvalds-declares-intel-fix-for-meltdown-spectre-complete-and-utter-garbage/)

Sorry I'm not more helpful.  BTW, nobody here is a paid Canonical employee. All volunteers.

---

### Post by Impavidus on 2018-02-07
> **Ronald_F._Guilmett said:**
> 
Which brings me to the main reason why I posted my set of questions, the most important of which you did not address at all:  Why is Canonical still only giving out Firefox 58.0.1?  It has been around eight days already since even the TheRegister knew that there were "critical" security flaws in that... flaws which are allegedly fixed in the 59.x.x release(s)... a Firefox release which has been generally and widely available already for at least the past 8+ days ?

I don't know where TheRegister got that information, but Firefox's website tells me that Firefox 58.0.1 was released 9 days ago and is the latest release. Firefox 59 is still beta. The release notes of 58.0.1 mention one security fix, only applying to Windows.

---

### Post by vasa1 on 2018-02-07
> **Impavidus said:**
> I don't know where TheRegister got that information, but Firefox's website tells me that Firefox 58.0.1 was released 9 days ago and is the latest release. Firefox 59 is still beta. The release notes of 58.0.1 mention one security fix, only applying to Windows.See [https://ubuntuforums.org/showthread.php?t=2384406](https://ubuntuforums.org/showthread.php?t=2384406) and my post there.

---

