---
title: "Cannot boot after installing VMWare"
date: 2013-02-04
forum: General Help
---

### Post by jmspiers on 2013-02-04
Hi folks,

I'm in a bit over my head with this one and I'm hoping someone can offer some help. I've done some Googling but so far haven't found a solution.

Machine:
* [Latitude E5420]("http://www.dell.com/downloads/global/products/latit/en/latitude-e5420-specsheet.pdf") (let me know what other details are needed for this problem)
* Ubuntu 12.04 x86

As the title says, I'm unable to boot into Linux. I did a couple of things shortly before the problem started:

1. Installed the latest updates (NOT version upgrade...standard updates). I didn't notice everything that was updated, but I rebooted afterwards and everything was fine. (I don't think the update was related to my problem but I still mention it just in case)

2. After rebooting I installed the latest version of VMWare player. It installed with no errors.

3. After installing VMWare player I noticed that I couldn't connect to a wireless connection at all (it hung on "Authenticating) and I could only stay connected to an Ethernet connection for a few seconds. In retrospect VMWare was probably the issue, but my first thought was that an update broke the gnome network manager (I had already downloaded VMWare before installing updates, so if an update messed up networking then I wouldn't have noticed right away). Because of that I uninstalled the gnome network manager and installed wicd instead. The problem persisted so I went ahead and rebooted. That's when I discovered that the OS wouldn't load.

When I try to boot into a recovery console this is what I see:
* If the laptop is plugged in it hangs on "Checking battery state...". There's no disk activity and it hangs indefinitely
* If the laptop is not plugged in then it gets past checking the battery state and immediately hangs on "Stopping System V runlevel compatibility"
* Sometimes if I leave it long enough it will occasionally spam a message about a wlan scan failing (unfortunately I didn't write it down and it's not replicating for me right now).

EDIT: I just reinstalled network-manager-gnome and now I see the message about the scan failing. This is what it says:

> * Stopping System V runlevel compatibility
* Starting Mount network filesystems
* Stopping Mount network filesystems
* Starting Mount network filesystems
* Stopping Mount network filesystems
[  69.633275] ERROR @wl_notify_scan_status : eth1 Scan_results error (-22)
* Stopping Read required files in advance

After that last message it just hangs.


The steps that I've tried so far are:
* Removing wicd and installing network-manager-gnome again (I had downloaded it before uninstalling it, just in case wicd didn't work)
* Booting into a previous version of Linux (hangs at the same place)
* Removing wicd and gnome-network-manager altogether
* Uninstalling VMWare

It would be easy to just nuke my install and start over, but I'm trying to improve my Linux skills so I'd prefer to fix the problem if possible. I also had just created a rather large VM that I didn't have a chance to backup and I'd prefer to not lose it. Does anybody have any advice?

Thanks in advance

---

### Post by jmspiers on 2013-02-04
Well I'm marking this as solved even though I didn't figure out what was going on. I ended up "fixing" the problem by doing a distro-upgrade to 12.10. After doing that Ubuntu booted successfully.

I'd still like to know what caused the original problem, but at least I'm up and running again so I'll call it good :)

---

### Post by henrx on 2013-02-05
VMWare has always given me troubel across two machines.  Virtual BOx works perfect every time.

---

### Post by dcstar on 2013-02-05
> **jmspiers said:**
> Hi folks,

I'm in a bit over my head with this one and I'm hoping someone can offer some help. I've done some Googling but so far haven't found a solution.

Machine:
* [Latitude E5420]("http://www.dell.com/downloads/global/products/latit/en/latitude-e5420-specsheet.pdf") (let me know what other details are needed for this problem)
* Ubuntu 12.04 x86
.........

[LIST=1]
[*]Firstly, why are you using 32-bit software when you have a 64-bit machine?
[*]Secondly, thousands of people install VMware Player without any issues, something went wrong with your install.
[*]Post Virtualization issues in the Virtualization forum, you get more help there than irrelevant comments from this forum.
[*]Created VMs run on any VM host platform, simply back up the files and restore them later.
[/LIST]

---

### Post by jmspiers on 2013-02-05
> **henrx said:**
> VMWare has always given me troubel across two machines.  Virtual BOx works perfect every time.

I also use Virtual Box and like it quite a bit, but I'm having trouble getting it to recognize my smart card reader. A quick Google search shows that it's a pretty common problem with VBox but people were saying they had success with VMware. I figured I'd give it a shot.

> **dcstar said:**
> [LIST=1]
[*]Firstly, why are you using 32-bit software when you have a 64-bit machine?[/LIST]

Because I wanted to :). Oh, and I was having some problems with 12.04 64-bit on my machine. It's irrelevant to my problem, but having a 64-bit processor doesn't mean you can't run 32-bit. I only have 4 GB of RAM so I didn't have a pressing need to use 64-bit.

> **dcstar said:**
> [LIST=2][*]Secondly, thousands of people install VMware Player without any issues, something went wrong with your install.[/LIST]

I have no doubt that something went wrong with my install (or with one of the updates right before the install). That's why I was posting here for help. Telling me what I already know is a waste of your valuable time. Nothing in my original post accused VMWare of having a bug.

> **dcstar said:**
> [LIST=3][*]Post Virtualization issues in the Virtualization forum, you get more help there than irrelevant comments from this forum.[/LIST]

The problem isn't related to virtualization. Please read the original post in its entirety before responding. Virtualization had absolutely nothing to do with my problem. The problem was that an update OR VMware (I'm not sure which) caused my laptop to be unable to boot. After upgrading to 12.10 I re-installed VMWare and I'm not having any problems. I suspect the original issue was caused by an update.

> **dcstar said:**
> [LIST=1][*]Created VMs run on any VM host platform, simply back up the files and restore them later.
[/LIST]

Hard to backup VMs when they're on an encrypted partition that you can't access. Yes, I probably could have recovered it, but as I said in my original post, I preferred to fix the problem in order to increase my Linux knowledge.

I'm not a Linux expert but I'm also not a Linux newb. I tried the simple stuff before posting here for help. If you're going to reply to posts then please actually provide support instead of making irrelevant and misguided comments.

---

### Post by dcstar on 2013-02-07
> **jmspiers said:**
> 
..........
I'm not a Linux expert but I'm also not a Linux newb. I tried the simple stuff before posting here for help. If you're going to reply to posts then please actually provide support instead of making irrelevant and misguided comments.

What is "irrelevant" about pointing out that you did not bother to try and fix the original problem rather than just install a fresh OS? Things do go wrong but it is impossible to try and help if you don't even bother to ask.

As far as "*Virtualization had absolutely nothing to do with my problem. The problem was that an update OR VMware (I'm not sure which) caused my laptop to be unable to boot."* VMware **IS** a Virtualization Platform (want to read **your** thread Subject?), and posting in that forum gets you access to people who know a lot more on the subject than will be in the General Forum.

Also make up your mind if you are "not sure" or "100% certain" about the same thing before bagging people trying to assist you.

**You** also specifically asked about recovering a VM you created and I gave you the answer - **you** did not mention any encryption previously and I am not a bloody mind-reader.

---

### Post by jmspiers on 2013-02-07
> **dcstar said:**
> What is "irrelevant" about pointing out that you did not bother to try and fix the original problem rather than just install a fresh OS? Things do go wrong but it is impossible to try and help if you don't even bother to ask.

OK this thread was resolved before you ever posted in it. You've obviously trolling and I shouldn't feed you, but I'll bite. After this I unsubscribe from the thread :)

Not quite sure why you keep posting on a thread that's resolved. Also not quite sure why you keep misreading what I'm writing. Where did I ever say that I installed a fresh OS? I recovered it far enough to boot as root and then did a distro upgrade. That's something that I was planning on doing anyway.

Also not sure what you mean by not even bothering to ask for help. Of course I asked for help. That's why I posted in the first place. Asking for help doesn't mean I'll stop trying to resolve the problem on my own. At least I was nice enough to make a follow-up post saying that help was no longer needed. You chose to write a completely unhelpful response to an issue that had already been resolved, but that's not my fault.

If you have thoughts on what caused the original problem then I'd love to hear them. Otherwise I'm sure you have better things you could be doing. I know I do.

> **dcstar said:**
> As far as "*Virtualization had absolutely nothing to do with my problem. The problem was that an update OR VMware (I'm not sure which) caused my laptop to be unable to boot."* VMware **IS** a Virtualization Platform (want to read **your** thread Subject?), and posting in that forum gets you access to people who know a lot more on the subject than will be in the General Forum.

I'm well aware of what VMware is. I didn't consider my problem to be related to virtualization but if you want to view it that way then that's certainly a valid opinion. If I thought the problem was VMware specific then I would have posted on the VMware forums. I thought the problem may have been triggered by installing it but that doesn't make it a problem with the program.

I think you're missing the larger picture, though. The issue that I was with your original reply is that you managed to ask several vaguely sarcastic questions, all of which hinted that I was an idiot who hadn't thought the problem through, and you provided absolutely no help. I'm guessing that you were just trolling but if you weren't then you may want to spend your time actually helping people instead of skimming their posts and then making irrelevant suggestions.

> **dcstar said:**
> Also make up your mind if you are "not sure" or "100% certain" about the same thing before bagging people trying to assist you.

Why on earth would I need to be 100% certain of something before getting on a support forum and asking for help? That's like going to a doctor and saying that I'm 100% sure that I have a cold and then turning around and leaving. If I didn't need the help then I wouldn't have posted in the first place. Having a specific problem doesn't mean I know what triggered it. If I did then I would be 99% of the way to solving it.

> **dcstar said:**
> **You** also specifically asked about recovering a VM you created and I gave you the answer - **you** did not mention any encryption previously and I am not a bloody mind-reader.

Can't speak for your mind reading abilities but you might want to work on your regular reading skills :). I never asked for help recovering a VM. I hadn't even tried it yet because my main goal was to fix the OS. In the end I recovered the VM and backed it up before upgrading. It's not like it was rocket science. I didn't mention anything about encryption because it was irrelevant. I can handle decrypting a drive. Again, not rocket science.

Unsubscribing from the thread now...feel free to have the last word :)

---

