---
title: "noobinfo: Script that helps novice users to share info, searching for issue solutions"
date: 2015-03-10
forum: General Help
---

### Post by GiovanniS on 2015-03-10
Hi,
I've written a really simple script that aim to generate a quite complete system report to share with a help request. This report is a collection of various ls* and dmesg messages, that are the information usually needed by gurus to solve hardware problems etc...

So, this script will help newbies to avoid to post something like: "My wifi dongle doesn't seems to work, what can I do?" without sharing the correct information about the system, hardware vendor, kernel loaded modules and so on.

Next, as suggest, I will add automatic post to a pastebin resource. For now it will generate a tar.gz collection of outputs and a single txt big file with all the report, uploadable to your favorite pastebin.

[https://github.com/LCyberspazio/noobinfo](https://github.com/LCyberspazio/noobinfo)


Have a nice day!

---

### Post by slickymaster on 2015-03-10
With no intention of diminishing you effort, which I consider meritorious, but just as a way of providing you some information, I just want to point you to the existence of [inxi]("https://packages.debian.org/sid/misc/inxi").

inxi is a full featured system information script that will detect information about hardware specifications, including but not limited to vendor details, CPU info, graphic and sound cards. Most importantly, it will output everything in a easy to read format and it can also be used on irc clients like irssi, weechat or xchat.

---

### Post by Holger_Gehrke on 2015-03-10
Three thoughts on this:
1) A fixed name for a temporary work directory is a bad idea. Use 'TARGET_TEMP_DIR=$(mktemp -d)' instead.
2) Why not get **all** the information the various tools offer ? Most of them have a '-v' option that enables additional output.
3) Instead of all the calls to various tools to list some subsystems, why not use 'lshw -sanitize' ? That would have the added advantage of removing serial-numbers and other identifiable information.

---

### Post by GiovanniS on 2015-03-10
@Slickymaster: Thanks for you info!

@Holger_Gehrke: thank you very much for your suggestions. I'm going to apply them to the code tomorrow! 

Thanks you all!

---

### Post by GiovanniS on 2015-03-10
Ok, 
I could not sleep without writing these modifications :D
I've uploaded a modified version of the script.
Updates include mktemp generated temporary directory, verbose ls*  command output and automatic upload of the report on the paste bin  arin.ga

Check it out [IMG]https://lqo-thequestionsnetw.netdna-ssl.com/questions/images/smilies/smile.gif[/IMG]

[https://github.com/LCyberspazio/noobinfo](https://github.com/LCyberspazio/noobinfo)

Have a nice day!

---

