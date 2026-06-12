---
title: "Am I Being Forced to Pay for a Support Package?"
date: 2016-07-01
forum: General Help
---

### Post by dellbuntu001 on 2016-07-01
This morning I updated my Ubuntu OS with Canonical's included software updater.

After resetting my machine the applications I was able to open became limited to just FireFox and VLC - the apps which I had (accidentally, but fortunately) left open while the updater ran. I suspect I can still open these apps, as their code was locked due to being open while the system updated.

From my investigation into a solution it appears this problem is already known and asked about, I saw a description which fitted exactly what I experienced on AskUbuntu.

Unfortunately I have problems with information overload these days due to health reasons. I found it too hard to follow what was being suggested on this thread, advice was all over the place and my ability to follow the conversation became hard. I looked elsewhere for help, did not find a suitable Email address on Canonical's site, and their online chat person told me I needed to buy 50 Ubuntu desktops and a support package before they would tell me how to fix the problem THEIR SOFTWARE created for me.

I thought Ubuntu was free. OK so yes pay for a support package, but when THEIR SOFTWARE UPDATER gives me the problems, it is a different scenario, surely. 

I have now discovered I also cannot plug in a USB stick, or download from the internet, because my disk is 'locked'.

So I ask this question:

Has Canonical put online a software updater which is designed to screw up people's machines, forcing them to paying for support?

If the answer is No, then I ask these questions:

Why is there a software updater which causes such problems allowed to persist online?

When will it be fixed?

If my system no longer lets me access the software updater, do I need to do a total reinstall of my OS?

So, just to add:

This is strongly reminiscent of how MicroSoft block illegal copies of Windows when the OS wants to go online to update. My copy of Ubuntu is not illegal surely? I was under the impression this was a free, open source OS.

---

### Post by speartip on 2016-11-23
A link to the ask ubuntu page which "fits exactly your experience" would be helpful, so that we can see in more detail what your issue is.
Ubuntu is free, & all the help & advise here is for free.
You've probably contacted the department that deals with Ubuntu at enterprise level, hence the "support package" advise.
The more detail you can give on here the better the replies.
Try with a simple:

```
sudo apt-get update
```

in a terminal, & post back the output, & let's see if that tells us anything.

---

### Post by vasa1 on 2016-11-23
> **dellbuntu001 said:**
> ... I saw a description which fitted exactly what I experienced on AskUbuntu.
....



Can you provide the Ask Ubuntu link? That may help shed some light on your issue.

---

### Post by howefield on 2016-11-23
Apologies, thread got messed up, trying to recreate.

dellbuntu001 posted the following..


After typing in your suggestion and my password, Terminal says:

```
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_i18n_Translation-en - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_dep11_Components-amd64.yml - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-backports_multiverse_dep11_Components-amd64.yml - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_binary-i386_Packages - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_binary-all_Packages - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_i18n_Translation-en%5fGB - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_i18n_Translation-en - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_dep11_Components-amd64.yml.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_dep11_icons-64x64.tar - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_binary-amd64_Packages.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_binary-i386_Packages.lz4 - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_binary-all_Packages - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_i18n_Translation-en%5fGB - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_binary-amd64_Packages - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_binary-amd64_Packages - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_binary-i386_Packages - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_i18n_Translation-en - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_dep11_Components-amd64.yml - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_dep11_icons-64x64.tar - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_binary-amd64_Packages - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_binary-i386_Packages - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_i18n_Translation-en - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_dep11_Components-amd64.yml - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_binary-amd64_Packages - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_binary-i386_Packages - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_i18n_Translation-en - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_dep11_Components-amd64.yml - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_dep11_icons-64x64.tar - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_binary-amd64_Packages - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_binary-i386_Packages - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_i18n_Translation-en - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_dep11_Components-amd64.yml - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_dep11_icons-64x64.tar - TransactionAbort (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_binary-i386_Packages - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_i18n_Translation-en - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_dep11_Components-amd64.yml - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_dep11_icons-64x64.tar - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_binary-amd64_Packages - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_binary-i386_Packages - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_i18n_Translation-en - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_dep11_Components-amd64.yml - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_binary-amd64_Packages - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_binary-i386_Packages - PrepareFiles (30: Read-only file system)
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/...nial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch http://archive.canonical.com/ubuntu/...nial/InRelease  Could not execute 'apt-key' to verify signature (is gnupg installed?)
E: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/...amd64/Packages  Could not open file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_binary-amd64_Packages.xz - open (30: Read-only file system) [IP: 91.189.88.161 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/di...amd64/Packages  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_xenial-security_main_binary-amd64_Packages.xz - open (30: Read-only file system) [IP: 91.189.88.161 80]
E: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/...amd64/Packages  Could not open file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_binary-amd64_Packages.xz - open (30: Read-only file system) [IP: 91.189.88.162 80]
W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (30: Read-only file system)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (30: Read-only file system)
W: Not using locking for read only lock file /var/lib/dpkg/lock
```

Now, as for the AskUbuntu thread, it came up as I started typing in my original thread subject, so I clicked into it to take a read. It was too much for me to take in, so I continued with my thread posting asking for the simple answer, as oppose to many suggestions and then people correcting what ought to be typed, etc.

I could be quite explicit, and ended up actually being so on AskUbuntu, about what I am actually suffering from in terms of being able to negotiate websites and other areas where I can get exposed to much more information than I am actually trying to find. I was there as it seemed I needed to be so as to be understood why I asked the question in the way to get a specific answer. I dont mind saying here what has happened a few years ago and why I have issues today, but I do not feel it relevant to the post.

From memory, the AskUbuntu post stated the poster had updated their system much as I had, and then when they clicked on the Ubuntu Software icon they got the circular 'loading app' mouse cusor, then it timed out and nothing loaded. This happened with my Ubuntu Software app, and all other apps on my launch bar, such as the LibreOffice apps. The thread then continued with suggestions, questions, revisions, etc, became too confusing like I have stated above.

However, now when clicking into the Ubuntu Software app it does actually load, hang on my screen for 2 seconds (yes I timed it) before it disappears. LibreOffice (etc) still does not load at all.

This whole thing has me massively out of joint with myself. Partly due to frustrations brought on by the sales person, and partly due to internal frustration - I used to be able to code websites and techy code was not an issue, but these days I need to be walked through it 

I need time out of the house and to be away from a computer for a while. I'm sorry but I do need this break.

However, Speartip, I would like to engage you in conversation about the Terminal output. By the time I return you may be offline, but I will be back to look at and to try any suggestions you may provide. If you need a further Terminal output tell me the Terminal input you'd like me to use, and I'll post it up for you 

Thank you, I've not read beyond Speartip's request but I feel like this is going to be more helpful than earlier efforts to gain a solution.

---

### Post by speartip on 2016-11-23
For some reason your root filesystem is being mounted as read only.
This can sometimes happen when you disk becomes corrupted. 
What are the specs of your computer? How old is it? How long has Ubuntu been installed? Were you doing anything unusual before this problem arose?
The more info you can give the better.

---

### Post by QIII on 2016-11-23
How did you install Ubuntu?  Is it running on an internal drive?

---

### Post by dellbuntu001 on 2016-11-23
Hi QIII,

I respect you are a super moderator and are lookiong to help. I cannot handle multiple conversation because I loose track very easily. This is the reason why I tried to obtain a tech support Email address, so that I could have a 'contained conversation'. I wish it were different, but I don't just have the head I used to have :( It's not so bad when it's somebody else's kit, but when it comes to my kit control of my emotions becomes very very hard sometimes, and then they get in the way of my objectivity. All I am able to do at present is recognise I have this problem, and to keep myself at minimum risk of outbursts, the sort which does nobody any good! ;)

I will answer the questions here, as they are valid and as Speartip say's, the more info the better.

But please, general request: can I have this conversation with just Speartip (unless another is nominated).

By all means, bounce comments around between yourselves, and within this thread is also fine, but to keep my focus I need to restrict myself to interacting with only one person at a time.

How did I install Ubuntu? I downloaded 16.04 as an iso, and created myself a bootable installation USB stick. I still have this for emergencies, so if it is a useful tool to correct the problem, I already have one :)

Is it running on an internal drive? Yes. Earlier this year my Dell Inspiron developed a hard drive problem, plus Microsoft were trying to force a Windows upgrade on me. I bought a hybrid drive and installed Ubuntu, as I have used Ubuntu previously, liked it a lot, and wanted to return to using it. It sort of became a 'win win' situation in that regard, almost like getting a new laptop with my favourite OS, have been very happy with it all since around Easter, until earlier this morning.

***********************************************************************************************************************************************************************************

Hi Speartip,

Some of your questions have just been addressed I believe, but I will elaborate further -

Dell Inspiron, bought refurbished so age is not known, I have had this laptop for 2 years myself. I've not kept up with processor progress over the last 12/13 years but maybe the processor will give you a clue to it's actual age.

Processor: Pentium(R) Dual-Core CPU T4500 @ 2.30GHz × 2 (64bit)
Graphics: Mobile Intel® GM45 Express Chipset
HD: 500GB Hybrid, bought new around April this year
RAM: 2.9GB

If you need more specs, do let me know what you'd like.

(As stated) Ubuntu installed around Easter this year, have been running it with zero issues since, until this morning. Have run the update/software installer a number of times to keep the OS and associated bits and pieces up-to-date and trim. This has always gone flawlessly.

Absolutely nothing unusual was being done with the computer; I use VLC to play back my meditation and yoga audio each morning before checking my Email. This morning was no different. Generally, I know what would strain or corrupt things, I have not mistreated this computer to my knowledge.

The only thing I can think of flagging up in this respect is, when I ran the updater I forgot to close both FireFox and VLC. However, if having these apps running (not being used, minimised and forgotten) while updating is bad for the system, I would have expected the code to include an 'open app check' with a request to close open apps if any are found before the updater app runs it's main operations.

I know I ought to have had them closed, and I guess this is a lesson for me to be more vigilant next time...

If my root file system has turned itself into read-only, can I boot Ubuntu from the USB stick and modify the HDD attributes back to how they ought to be? If so this is a process I do understand, but would need direction to be able to do it properly.

My head is frazzled, but I'll check back tomorrow. This may not be til later in the afternoon, but this so far has been so much more a pleasant experience compared to trying to unpick the threads in AskUbuntu and the conversation with the sales lady. I thank you for your concern and willingness to help :)

Best regards

Mark

---

### Post by lisati on 2016-11-23
As is the case with AskUbuntu, the advice offered here is free. One advantage of posting your queries here in a public forum is that one of the many volunteers here might have seen something that is sufficiently similar to the problems you're experiencing to be able to offer some useful suggestions.

---

### Post by QIII on 2016-11-23
@dellbuntu001:

While I understand what you are saying and will step back myself, I will ask you ***not to make demands of the community as to the manner in which support is given***. You are seeking help with an issue, I understand.  But this is not a private session between you and speartip and with a community of two million members, it is not unlikely that others will have an issue identical or similar to yours.  The questions asked and support given are ***theirs***, too.  This is a community.

---

### Post by speartip on 2016-11-23
@dellubuntu001:
I totally agree with QIII.
The more people that chip in here the better. There will probably be others on the forum far more qualified in this matter than me.
This is not a problem I have encountered before, but others may have.

Anyway to your problem. That Laptop is fairly old, in which case hard drive failure is a strong possibility. If, as you say you still have a bootable usb, it might be an idea to use it. Boot into it and run a program called "disks". When the program opens, highlight the hard disk that ubuntu is installed on, in the left hand column. Then in the top right, you'll see an icon. Click it & click "SMART Data & self-tests". In the new window click "start self test" & "extended". Enter your password & let it run. When finished let us know what the "overall assessment" says. This isn't fool proof, but will give a good idea on the state of your hard drive.

---

### Post by dellbuntu001 on 2016-11-24
I see your point. Please understand I have an Asperger diagnosis which has been exaggerated by mild brain damage from something that happened a few years ago.

I am not as able minded as you may assume an average poster here to be.

I would normally go through a process like this with a support worker, who would be talking on my behalf. But, in this has not been planned into the support schedule as it was not a planned progression/event... and I need to try and relearn how to do these things by myself.

I was trying to avoid forum help as I know I have some social issues which make it a bad medium for me to gain help from. I originally only wanted a tech support Email address to have this conversation. Maybe this can be conducted by Private Message?

I would like to reach mutual understanding and a comfortable compromise, is that OK?

---

### Post by speartip on 2016-11-24
I understand your problem. And so will everyone else on here. Don't worry we'll be as patient as you need. The reason these things are done on the forum & not privately, is so anyone else with the same issue, can see how it gets resolved (if indeed it does) & learn themselves.
 Are you able to follow the procedures in the 2nd half of my post?

---

### Post by dragonfly41 on 2016-11-24
OP wrote > [COLOR=#000000]However, Speartip, I would like to engage you in conversation about the Terminal output.[/COLOR]
OP's need to focus on one point of contact is understood.
So, @speartip, it seems that you have been nominated as spokesperson in this thread.

OP agrees that we can interchange ideas but you will be the chairperson to decide whether to advise OP on  the road map forward.

One suggestion I have, @speartip, is to go back to read the clues in post #4.

```

W: Problem unlinking the file /var/lib/apt/lists/partial/... ... ...
W: Problem unlinking the file /var/lib/apt/lists/partial/... ... ...
W: Problem unlinking the file /var/lib/apt/lists/partial/... ... ...
W: Problem unlinking the file /var/lib/apt/lists/partial/... ... ...
W: Problem unlinking the file /var/lib/apt/lists/partial/... ... ...

```

This long list of &#8220;problem unlinking the file(s)&#8221; suggests that perhaps purging some caches in above apt paths might help the situation.

The files can be viewed here in browser ...

file:///var/lib/apt/lists/partial/

One suggestion is to remove all files in &#8220;/var/lib/apt/lists/partial/&#8221; folder and again run sudo apt-get update.

```

sudo rm -rf /var/lib/apt/lists/partial/* && sudo apt-get update

```

Reference: [http://askubuntu.com/questions/615407/vivid-apt-get-update-huge-package-files-in-var-lib-apt-lists-partial](http://askubuntu.com/questions/615407/vivid-apt-get-update-huge-package-files-in-var-lib-apt-lists-partial)

Also there is a useful tool - Y PPA Manager - for cleaning up PPA installations which can be installed using the instructions here ..

[https://launchpad.net/~webupd8team/+archive/ubuntu/y-ppa-manager](https://launchpad.net/~webupd8team/+archive/ubuntu/y-ppa-manager)

```

sudo add-apt-repository ppa:webupd8team/y-ppa-manager
sudo apt-get update

```

After installation Y PPA Manager is found under System Tools menu (right at the bottom).

On launching click on the Advanced tab for cleaning up options.
But I suggest that you try this @speartip before advising OP

...

Incidentally, I am using a very antiquated Dell 1720 laptop so I don't think that these symptoms (above) necessarily reflect a hardware (disk) problem.

---

### Post by speartip on 2016-11-24
@dragonfly41, Thanks for your input. You make a good point. Ideally the /partial folder should be empty. I was concentrating more on the fact that Ubuntu will mount the root system as read only, when there are disk errors. It makes sense to follow your suggestion first.

@dellubuntu001. If you have followed the advise in my last thread, then please post the output here. Regardless, dragonfly41 makes a good point. If you log back into your system, & in a terminal run:
```
sudo rm -rf /var/lib/apt/lists/partial/* && sudo apt-get update
```
Let's see where that leaves us.

---

### Post by The Cog on 2016-11-24
@speartip:
I find the error messages at the bottom of the output in post #4 (Read-only file system) worrying. I think fixing this might be a good first step, and would probably suggest running fsck on the relevant partition from a live CD.  From the live CD, run <b>sudo parted -l</b> to list the drives and partitions, then run "sudo fsck /dev/sda5" or whatever partition needs fixing up.

---

### Post by speartip on 2016-11-24
@ The Cog. Agreed. I'm also now thinking that the command in #14 maybe won't work with the file system being read only.
Think I'll wait for the op to post back on what He has/hasn't tried yet first.

---

### Post by dellbuntu001 on 2016-11-24
I appreciate your understanding, thank you everybody for your patience :)

@Dragonfly thank you for your intervention :)

@Speartip your guidance is much appreciated, yes I can probably follow any set of instructions you request, that is easy. What isn't is keeping my eye on what I need to be following...

> **speartip said:**
> If you have followed the advise in my last thread, then please post the output here. Regardless, dragonfly41 makes a good point. If you log back into your system, & in a terminal run:
```
sudo rm -rf /var/lib/apt/lists/partial/* && sudo apt-get update
```
Let's see where that leaves us.

I'll go run the extended self test in a second. I thought I'd post the requested terminal output first, given it was the quickest piece of info to retrieve. I'm not sure if it ought to be in a CODE or a QUOTE box, I used QUOTE last time and will do so again. If this is wrong please advise.

[QUOTE=Terminal]
ad-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_xenial-security_restricted_i18n_Translation-en - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_xenial-security_restricted_dep11_Components-amd64.yml - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_xenial-security_universe_binary-amd64_Packages - PrepareFiles (30: Read-only file system)
W: Problem unlinking the file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_xenial-security_universe_binary-i386_Packages - PrepareFiles (30: Read-only file system)
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Could not execute 'apt-key' to verify signature (is gnupg installed?)
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/xenial/InRelease](http://archive.canonical.com/ubuntu/dists/xenial/InRelease)  Could not execute 'apt-key' to verify signature (is gnupg installed?)
E: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/xenial-backports/restricted/binary-amd64/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/xenial-backports/restricted/binary-amd64/Packages)  Could not open file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_binary-amd64_Packages.xz - open (30: Read-only file system) [IP: 91.189.88.161 80]
E: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/xenial-updates/main/binary-amd64/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/xenial-updates/main/binary-amd64/Packages)  Could not open file /var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_binary-amd64_Packages.xz - open (30: Read-only file system) [IP: 91.189.88.149 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/main/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/xenial-security/main/binary-amd64/Packages)  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_xenial-security_main_binary-amd64_Packages.xz - open (30: Read-only file system) [IP: 91.189.88.149 80]
W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (30: Read-only file system)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (30: Read-only file system)
W: Not using locking for read only lock file /var/lib/dpkg/lock
[/QUOTE]

Before it reached these line it spewed out a lot more, but I assume it is only this last section which is relevant.

So far so good. I do feel much more objective today, have had a good talk about this with support today so I expect my objectivity to remain. Maybe not for too much longer tonight but on the subject ongoing.

I'll now go reboot from USB and report back shortly :)

---

### Post by dragonfly41 on 2016-11-24
@speartip, your earlier observation in post#5 > For some reason your root filesystem is being mounted as read only.
This can sometimes happen when you disk becomes corrupted.  is bang on the nail.

Searching > (30: Read-only file system) throws up similar scenarios.

Perhaps now suggest that OP runs ```
mount -t ext4
``` to inspect the mounted ext4 partition(s).

Partition should be mounted rw (read, write).

---

### Post by speartip on 2016-11-24
@dellbuntu001. It does sound like the problem is a corrupt drive. If you read this while using your live usb, & know what partition you have ubuntu installed on. (sda1/2/3 or hda1/2/3 etc) open a terminal &:
```
sudo fsck /dev/sdaX
``` - Where X is the number of your partition.
That should tell us if the drive is clean or not.

---

### Post by dellbuntu001 on 2016-11-24
I have some more data, I'm running on Live via USB currently as the HD does not boot now.

I went to Disks but was not able to find any SMART test option. I checked in the help file to see if I was looking at the right bit, and I also wrote down what I could see in the 'gear button' menu for reference. I don't think this matters much as that was before I tried rebooting the HD. I have two error messages which may be of use. I'll not be able to do much more this evening but I will have a lot more time tomorrow. I might be able to run that last sudo command after typing -

> **BootSequence_#01]
/dev/sda1 contains a file system with errors, check forced.
Inodes that were part of a corrupt orphan link lost found

/dev/sda1: UNEXPECTED INCONSISTENCY said:**
> 

[QUOTE=BootSequence_#02]
/dev/sda1 contains a file system with errors, check forced.
[  4.276127] ata1.00: exemption Emask 0x0 SAct 0x0 action 0x6.2%
[  4.276164] ata1.00: BMDMA stat 0x25
[  4.276188] ata1.00: failed command: READ DMA
[  4.276220] ata1.00: cmd c8/00:08:b0:41/00:00:00:00:00/e4 tag 0dma 4096 in
                               res 51/84:00:b6:b0:41/00:00:00:00:00/04 Emask 0x10 (ATA bus error)
[  4.276296] ata1.00: status: {DRDV ERR}
[  4.276322] ata1.00: error: {ICRC ABRT}
Inodes that were part of a corrupt orphan link lost found

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
      (i.e., without -a or -p options)
fsck exited with status code 4
The root file system on /dev/sda1 requires a manual fsck


There may be some typos but I can be quite good with detail, maybe that'll help home in a bit better on the problem. I'm quite interested to run a manual fsck, but I have no idea what it is! :confused:

Yep, I think I can run the next next sudo command and paste the o/p, but I'll have to call that a night on this, hope that ok...

---

### Post by dellbuntu001 on 2016-11-24
Ah, so that's the manual fsck command, it says:

[QUOTE=Terminal]
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  Fix<y>? 
[/QUOTE]

I assume I ought to say Yes, but I'll leave this for tomorrow to confirm. Sorry if that's a cliff-hanger food and rest is needed.

Many thanks all :)

---

### Post by speartip on 2016-11-24
@ dellbuntu001
As expected, corrupt filesystem.
Run it again tomorrow, answer yes. Hopefully this will make your filesystem writeable again.
Then log back into Ubuntu & run the command in #14.

---

### Post by him610 on 2016-11-24
FWIW:
> Processor: Pentium(R) Dual-Core CPU T4500 @ 2.30GHz × 2 (64bit)

CPU is about 8 to 10 years old.

---

### Post by dellbuntu001 on 2016-11-25
[QUOTE=Terminal]
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  Fix<y>? yes
Inode 2883718 was part of the orphaned inode list.  FIXED.
Inode 2883719 was part of the orphaned inode list.  FIXED.
Inode 2883720 was part of the orphaned inode list.  FIXED.
Inode 2883721 was part of the orphaned inode list.  FIXED.
Inode 2883722 was part of the orphaned inode list.  FIXED.
Inode 2883723 was part of the orphaned inode list.  FIXED.
Inode 9700901 was part of the orphaned inode list.  FIXED.
Inode 9707090 was part of the orphaned inode list.  FIXED.
Inode 9708216 was part of the orphaned inode list.  FIXED.
Inode 9708244 was part of the orphaned inode list.  FIXED.
Deleted inode 9708496 has zero dtime.  Fix<y>? 
[/QUOTE]

Do I delete Inode 9708496? And, assuming there are other Inodes which get flagged for deletion, do I treat them all the same (Yes to all or No to all)?

I'm not quite sure what you mean by

[QUOTE=Speartip]Then log back into Ubuntu & run the command in #14[/QUOTE]

I understand I'm to run the manual fsck again, after booting and logging into the install on sda1, which following you advice I believe will shortly be possible.

I don't get what you mean by running the command in #14 however, can you elaborate on what that is please?

@him610 8 to 10 years old? Thank you, I like to know the trivia of my hardware. I didn't know it was quite that old, I thought it may have been about half that.

- Today I am quite stable again, and have all my wits about me, I think I can handle a conversation with more than just one person in regard to this computer now...

So the file system got corrupt. The HD is only about 7 months old so I find it hard to see it being a hardware issue with the HD. I can accept that the occasional new HD will go wrong quicker than expected; there will be some quality variation in manufacture I'm sure.

So, for the sake of completeness: assuming the actual HD is not at fault, and this problem appears to be triggered by an O/S update; is there anything known that can cause the problem described here, and is there any advice on how to avoid such problems?

---

### Post by speartip on 2016-11-25
Hi dellbuntu001.
It is best that you answer Yes to all the "fix" questions.
It wouldn't harm to run:
```
sudo fsck /dev/sda1
``` command again to see if all the errors have gone & the filesystem is now clean.
After that log back into your system & run the command given in post 14 of this thread:
```
sudo rm -rf /var/lib/apt/lists/partial/* && sudo apt-get update
```
hopefully we will be getting somewhere.

As to your observation about the cause of this problem. It's highly unlikely the update caused this, as the forum would be full of others with the same issue. 
Somehow your filesystem has become corrupted. A power outage could cause this or a number of other things.
Let's try & get this sorted first & deal with that later.

---

### Post by dellbuntu001 on 2016-11-25
[QUOTE=Terminal]
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
/dev/sda1: clean, 274856/30334976 files, 33257650/121319680 blocks
ubuntu@ubuntu:~$ 
[/QUOTE]

- Leaving my USBuntu stick, hopefully will be posting next using the HD install...

---

### Post by dellbuntu001 on 2016-11-25
> **speartip said:**
> 
After that log back into your system & run the command given in post 14 of this thread:
```
sudo rm -rf /var/lib/apt/lists/partial/* && sudo apt-get update
```


I see, no problem. Login was successful, terminal o/p for the above command is:

[QUOTE=Terminal]
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]
Get:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages [177 kB]
Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [426 kB]
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages [172 kB]
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Translation-en [71.2 kB]
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [66.9 kB]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [38.3 kB]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [19.4 kB]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [25.6 kB]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse amd64 DEP-11 Metadata [212 B]
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse DEP-11 64x64 Icons [29 B]
Get:16 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [420 kB]
Get:17 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main Translation-en [164 kB]
Get:18 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [293 kB]
Get:19 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [182 kB]
Get:20 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [365 kB]
Get:21 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [362 kB]
Get:22 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe Translation-en [132 kB]
Get:23 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [119 kB]
Get:24 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [137 kB]
Get:25 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [2,520 B]
Get:26 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/multiverse DEP-11 64x64 Icons [7,765 B]
Get:27 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 Packages [4,392 B]
Get:28 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/main i386 Packages [4,400 B]
Get:29 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [208 B]
Get:30 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/main DEP-11 64x64 Icons [29 B]
Get:31 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [212 B]
Get:32 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/universe DEP-11 64x64 Icons [29 B]
Get:33 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/multiverse amd64 DEP-11 Metadata [212 B]
Get:34 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/multiverse DEP-11 64x64 Icons [29 B]
Fetched 3,497 kB in 4s (755 kB/s)   
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
[/QUOTE]

[QUOTE=Speartip]
As to your observation about the cause of this problem. It's highly unlikely the update caused this, as the forum would be full of others with the same issue. 
Somehow your filesystem has become corrupted. A power outage could cause this or a number of other things.
Let's try & get this sorted first & deal with that later.[/QUOTE]

OK, there was no power outage that I saw, everything I observed with the laptop was exactly as it has been for months, the only variable was the update. Given I now know how old the laptop is I can see how something internal may have misbehaved.

But yes, leaving that for the moment, what is next best to do?

---

### Post by slickymaster on 2016-11-25
> **dellbuntu001 said:**
> I see, no problem. Login was successful, terminal o/p for the above command is:```
Hit:1 http://archive.canonical.com/ubuntu xenial InRelease
Hit:2 http://gb.archive.ubuntu.com/ubuntu xenial InRelease
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:5 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB] 
Get:6 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [177 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [426 kB]
Get:8 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages [172 kB]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en [71.2 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [66.9 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [38.3 kB]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [19.4 kB]
Get:13 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [25.6 kB]
Get:14 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [212 B]
Get:15 http://security.ubuntu.com/ubuntu xenial-security/multiverse DEP-11 64x64 Icons [29 B]
Get:16 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [420 kB]
Get:17 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [164 kB]
Get:18 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [293 kB]
Get:19 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [182 kB]
Get:20 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [365 kB]
Get:21 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [362 kB]
Get:22 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [132 kB]
Get:23 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [119 kB]
Get:24 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [137 kB]
Get:25 http://gb.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2,520 B]
Get:26 http://gb.archive.ubuntu.com/ubuntu xenial-updates/multiverse DEP-11 64x64 Icons [7,765 B]
Get:27 http://gb.archive.ubuntu.com/ubuntu xenial-backports/main amd64 Packages [4,392 B]
Get:28 http://gb.archive.ubuntu.com/ubuntu xenial-backports/main i386 Packages [4,400 B]
Get:29 http://gb.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [208 B]
Get:30 http://gb.archive.ubuntu.com/ubuntu xenial-backports/main DEP-11 64x64 Icons [29 B]
Get:31 http://gb.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [212 B]
Get:32 http://gb.archive.ubuntu.com/ubuntu xenial-backports/universe DEP-11 64x64 Icons [29 B]
Get:33 http://gb.archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata [212 B]
Get:34 http://gb.archive.ubuntu.com/ubuntu xenial-backports/multiverse DEP-11 64x64 Icons [29 B]
Fetched 3,497 kB in 4s (755 kB/s) 
**[COLOR=#b22222]AppStream cache update completed, but some metadata was ignored due to errors.[/COLOR]**
Reading package lists... Done
```
<---snip--->
@speartip:
Just as a heads up. That's a already reported bug: [https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1644498](https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1644498) which was also reported before: [https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1575248](https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1575248)

---

### Post by speartip on 2016-11-25
@slickymaster. Thanks for that, was wondering what that was myself. Probably best just ignored in this case.

@dellbuntu001. Things are looking a lot better now. Now run: ```
sudo apt-get upgrade
``` and your system should update, and your good to go.

---

### Post by dellbuntu001 on 2016-11-25
OK, It looks like it's all back to normal 8D

Many thanks for your help Speartip, and to all else who contributed, very much appreciated :) :)

I apologise again for asking for help in a specific way. I feel this exercise has me prepped to be able to handle a help thread conducted in the way you are used to... there is less fear of having more information offered than I am able to take in, and less fear of code I don't know too.

Unless there is more to do, any chance we can discuss what may have caused the problem? I understand there is doubt about the updater causing the problem, but I doubt the hard drive is at fault. Given the machine is as old as him610 suggests, could it be component issues elsewhere?

---

### Post by dellbuntu001 on 2016-11-25
I'm happy to be proved wrong about the HD being at fault by the way, but I would need to see a test result saying so to be convinced at this point. If there is a test, let me know how to run it please :)

Oh - ought we need to start a new thread for this?

---

### Post by dragonfly41 on 2016-11-25
Start by reading through here ..

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

Install monitoring tools by running these three separate commands.

```

sudo apt-get install gsmartcontrol
sudo apt-get install smartmontools
sudo apt-get install smart-notifier

```

(some of the above might already be installed).

Then before proceeding with tests first check that your disk device (/dev/sda) has (so called) SMART capability
by running this command.

```

sudo smartctl -i /dev/sda 

```

After you post the output from this last command we can explain later how you might apply these disk testing tools.

[I]Be warned that the output from some of the logs might be difficult to understand by other than a disk engineer
but as a user you are just looking for just broad warnings if the device in approaching failure.[/I]

---

### Post by speartip on 2016-11-25
Hi dellbuntu001.
I'm glad your problem seems to be solved. As to the cause, I really wouldn't worry about it, unless it happens again. (or follow Dragonfly41s advise above)

Just 3 things you may want to think about though.

1. Check the hard drive by using the "disks" program as per post 10. (the icon you're looking for is either 3 dots or 3 lines)

2. In future it may help to update your system via a terminal rather than the software centre, as you have now done, with the "sudo apt-get update" & "sudo apt-get upgrade" commands. That way if there are any errors, the terminal will tell you what the issue is.

3. Make sure all your important info. is backed up, just in case there is any future problem with your computer, that may not be resolvable.

Thanks to all who helped Me & dellbuntu001 with this issue.

---

### Post by dellbuntu001 on 2016-11-25
@drangonfly41 - SMART test (long) is running, need to wait 101 minutes, but I need to go out before the test will end, thanks for the link to the Smart monitoring tools :) I'll get back here later with the results.

@Speartip - Disks doesn't seem to want to provide me with the SMART option; this time I loaded Disks from the installation (as oppose to Live from the USB) and the options in the 'gear button' menu (which the help file tells me to look in) are the same as they were when I looked at this last night whilst running Live from the USB, they are as follows:

- Format Partition
- Edit Partition
- Edit File System
- Change Passphrase (greyed out)
- Edit Mount Options
- Edit Encryption Options (greyed out)
- Create Partition Image
- Restore Partition Image
- Benchmark Partition Image

Could my copy of Disks be missing some components?

I have back-ups of most things, but it never hurts to be reminded, I ought to back up my college folder on my MacBook - something I'll get going before going out.

Run my updates from the terminal? OK cool, I can do that.

_________________________________________________________________________________

With regard to the terminal, it's not that different to how I remember DOS. I''ve never really got to grips with DOS and I don't know a lot about the command functions in terminal. Where best can I learn about this type of code, and does it have a name?

---

### Post by speartip on 2016-11-25
@dellbuntu001. That's the Menu you get when you click the cog under the graph of your disk partitions.
This is what you're looking for:
[ATTACH=CONFIG]272373[/ATTACH]
Not to worry though, dragonfly41s command is doing the same thing.

---

### Post by dellbuntu001 on 2016-11-26
It's not appearing to be returning results; I've tried running the test twice now, the last time it ought to have finished at 8pm yesterday, but I've left the terminal window open all night and right up until now (it's still open) and there has been nothing more displayed since it started and gave a stop time.

I've now got Disks doing the check, thanks for the pointer. I think the Help File people might want to take a look at the directions to that menu, I am sure I got referred to the button with cogs on it. Cant check currently as Disks is locked while it's running the test, but I will to confirm once the test it done.

---

### Post by dragonfly41 on 2016-11-26
I cannot comment on the Disks app interface (UI) for Ubuntu 16.04 because I'm using Ubuntu 14.04 which has a different UI.

It is possible that your disk device is not SMART enabled and so the tests will not run.

You can try to enable SMART by running command

```
sudo smartctl --smart=on /dev/sda
```

Or SMART might be enabled via the BIOS.

Try this test command to output temperature of your disk device.

```
sudo hddtemp /dev/sda
```

More here .. [https://wiki.archlinux.org/index.php/S.M.A.R.T](https://wiki.archlinux.org/index.php/S.M.A.R.T).

And a helpful blog .. [https://www.thomas-krenn.com/en/wiki/Analyzing_a_Faulty_Hard_Disk_using_Smartctl](https://www.thomas-krenn.com/en/wiki/Analyzing_a_Faulty_Hard_Disk_using_Smartctl)

...

P.S. My SMART tests are either 2 minutes (short) or 2 hours (long) in duration.

---

### Post by dellbuntu001 on 2016-11-28
Disks came through with a diagnostic, looks like it is talking about disk errors, but I'm not too sure how to interpret the results. Well, I say that, it is quite clear it is talking about old age, but this drive is only 7 months old, My studio PC in the other room is running on PATA drives from years ago (they need to be changed, but just to say...):

[ATTACH=CONFIG]272433[/ATTACH]

As for Disk's Help File, I include what I find misleading here:

> **Disks_Help_File]
[COLOR=#6C6C6C][FONT=sans-serif]**[B]Check your disk's health using the Disks application**

[/B][/FONT][/COLOR]
[COLOR=#3C3C3C][FONT=sans-serif]
[LIST]
[*]Open *Disks* from the [COLOR=#6C6C6C]Activities[/COLOR] overview. 
[*]Select the disk you want to check from the list of storage devices on the left. Information and status of the disk will be shown. 
[*]Click the gear icon and select [COLOR=#6C6C6C]SMART Data & Self Tests&#8230 said:**
> . The [COLOR=#6C6C6C]Overall Assessment[/COLOR] should say "Disk is OK". 
[*]See more information under [COLOR=#6C6C6C]SMART Attributes[/COLOR], or click the [COLOR=#6C6C6C]Start Self-test[/COLOR] button to run a self-test. 
[/LIST]
[/FONT][/COLOR]


I interpret the 'gear icon' to be the button with the cogs on it, not the three lines icon SpearTip advised upon earlier.

Here is what I see when Disks is open. 
 [ATTACH=CONFIG]272434[/ATTACH]
Notice, at the bottom left of the Volume displayed are three icons/buttons. A square (stop), a horizontal line, and then the cogs.

Anyway. I'm not worried about that really, but somebody who edits help files may want to amend this part of the Disks help file so it is clearer, this is just to flag it up :)

What do you see in the hard drive test results?

---

### Post by mastablasta on 2016-11-28
SMART is showing a used but an OK disk. however, SMART is not always that smart. it can not see certain issues. my disk passed SMART eventhough it had trouble booting and made strange noises. 

bad disk SATA cable can also cause corrupted file system. 

avoid upgrading over wi-fi - while it normally Works fine it can cause issues occasionally when file is not propperly downloaded. wired connection is far more reliable and less prone to any transmission errros.

file system is thrown into read-only mode in order to protect your data.

---

### Post by QIII on 2016-11-28
@Dellbuntu001:

Your disk test is indicating all is well.  The "Type" column indicates the type of test and the "Assessment" column gives the results.  Those all say "OK".

Are you able to do your updates now?

---

### Post by dellbuntu001 on 2016-11-28
@mastablasta - I only use wifi for devices which have no ethernet port, this does and it wired. I will remember that as useful info tho :) I think the way the HD fits into this chassis could be a lot better. You mention SATA cables, although not via a cable but via a connector block are you suggesting this could be a cause?

@QIII Everything seems normal now thanks, both with the computer and with my head ;) I've even still got the original problem I was trying to solve: VLC turns it volume to 0 or near 0 when going from item to item on the playlist. This is random, or at least I've yet to notice any particular pattern. I was going to un-install and re-install it to see if that would work. I thought I'd update my system before doing so, and the rest is pretty much displayed here.

I have since tried the fix with VLC, but even freshly installed it does the same. It didn't for quite some time, this is only a problem of the last 6 weeks or so. If I don't find anything about this here (when calm I am quite capable, it's when in crisis my mind goes) where best do you suggest I start a thread for this?

---

### Post by The Cog on 2016-11-28
I doubt whether reinstalling VLC will make any difference because it's just replacing the application code. Your configuration settings don't get removed by this installation process.
Your vlc settings are held in your home directory in ~/.config/vlc. Renaming or deleting this directory will blow away your personal vlc settings that may be causing you issues, so that is probably worth trying.

---

### Post by dellbuntu001 on 2016-12-02
Found it and renamed as suggested... VLC now opens with '0' as it's default volume setting it seems. It may take a day or two to see if it still resets the volume to '0' when moving between playlist items (given this was an intermittent fault previously).

However, the config file looks interesting, the issue may be resolvable by looking at that more carefully. I may well venture down this way next week, if I need some additional help in locating the correct part of the file to edit, I'll start a new thread :)

Cheers! :)

---

