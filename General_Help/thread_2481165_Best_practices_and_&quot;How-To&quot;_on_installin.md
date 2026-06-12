---
title: "Best practices and &quot;How-To&quot; on installing packages outside of version repository?"
date: 2022-11-20
forum: General Help
---

### Post by DVD-R on 2022-11-20
Hello All,
I hope I've posted this question in the correct forum category.

I'm currently stuck with a 32bit laptop as my PC
Ubuntu 16.04 is the latest release supporting 32bit architecture
Ubuntu 16.04 of course goes back a few years.
Package developers (outside of the a Ubuntu version's repository) in all probability will no longer provide a package repository applicable to an older version of Ubuntu.

For example - the Pale Moon browser is of interest.
Back when Ubuntu 16 was the latest release - the Pale Moon people provided a repository one could manually add and then download the program.
At some point the Pale Moon people dropped that repository.

From what I understand - the only way one would acquire an older version of Pale Moon - would be to download a tar file and build it.
I need to understand how that process works - and if Pale Moon version 28 would be compatible with Ubuntu 16.04 32bit

Can anyone point to general information that I could study and learn best practices on that process?

Sincere thanks!

---

### Post by ian-weisser on 2022-11-20
> **DVD-R said:**
> Ubuntu 16.04 is the latest release supporting 32bit architecture

That's not quite accurate.

18.04 had a 32-bit install image (.iso).

Many 32-bit libraries are still in the Ubuntu repositories and fully supported. It's still possible to assemble a 32-bit desktop from packages in the Ubuntu repositories. It's just that a complete 32-bit desktop is no longer tested by our very limited number of volunteer 32-bit testers and developers, so a complete install image (.iso) based upon that missing hard work is no longer produced.

> **DVD-R said:**
> From what I understand - the only way one would acquire an older version  of Pale Moon - would be to download a tar file and build it. 

Well, [http://linux.palemoon.org/](http://linux.palemoon.org/) suggests that you have perhaps misunderstood. **No building**. Clear (optional) install instructions. And deb packages available:

> It is **not** necessary to install Pale Moon to use it. Pale Moon for Linux is distributed as a [xz-compressed tarball]("http://linux.palemoon.org/download/mainline/")  that can be extracted and run from any location on your system. If  however you prefer to "install" it on your system, you can find  instructions to do so [here]("http://linux.palemoon.org/help/installation/").

  Additionally, you can install one of these fully-endorsed third-party builds of Pale Moon for Linux:
  
[LIST]
[*]Pale Moon repositories for Debian and Ubuntu: [Original GTK+ 2]("https://build.opensuse.org/package/show/home:stevenpusser/palemoon") or [GTK+ 3]("https://build.opensuse.org/package/show/home:stevenpusser:palemoon-GTK3/palemoon") -- maintained by Steve Pusser 
[/LIST]


---

### Post by DVD-R on 2022-11-21
Thanks
I looked at the instructions for Pale-Moon and it appears to me that they are having one download a tar file and build it.
I tried the instructions ([http://linux.palemoon.org/help/installation/](http://linux.palemoon.org/help/installation/)) and each step appeared to work ok

But within the instructions there is an assumption that a folder and its contents will be built "/usr/bin/palemoon"
No such folder exists and I am not familiar enough with those steps to know why.
I really need some kind of material I can study to understand what these steps are doing.

---

### Post by DVD-R on 2022-11-21
Ok - I just watched a youtube video - which explained how to run an application extracted from a  tar.bz2 file.
I do have palemoon running.
I think the instructions assumed I would know how to do that - and the instructions they were providing had to do with making links to the palemoon file in order to execute it.
I'll research further and see if I can't try to understand what those instructions are doing.
Thanks!


Ok - I watched another video on how the .deskop file protocol works - and have created a launcher on the desktop with the palemoon icon showing.
So far so good! :-]

---

### Post by ian-weisser on 2022-11-21
Please clearly quote exactly which steps you want explanations of. Quote, not describe.

Fair warning: Our first question will usually be "*did you read the manpage for that command?*"

---

### Post by DVD-R on 2022-11-21
Thanks!

Here is one:

Create a symbolic link /usr/bin/palemoon that points to ~/palemoon/palemoon:
ln -s ~/palemoon/palemoon/usr/bin/palemoon

In my case:
1) I extracted all of the palemoon files within  /home/user/.palemoon/palemoon
2) There is no folder within the system as usr/bin/palemoon
3) I kind of understand the reason for a symbolic link - it functions as a pointer to a file - so that that file can be executed from a different directory
But I don't know enough about system files to understand why a link would be created for usr/bin/palemoon

Anyway - I attempted the following:
ln -s ~/.palemoon/palemoon/ usr/bin/palemoon

The system response is "No such directory"
Which I assume is the system's way of saying the usr/bin/palemoon directory does not exist

However I just did that command again and got the system response:
ln: failed to create symbolic link '/usr/bin/palemoon': File exists


But if I type palemoon in the home directory within the terminal the system response is:
palemoon: command not found

So if I understand how the symbolic link is supposed to work - it doesn't
Sincere thanks for your help

---

### Post by ian-weisser on 2022-11-21
> **DVD-R said:**
> 
Anyway - I attempted the following:
ln -s ~/.palemoon/palemoon/ usr/bin/palemoon


That directory does not exist because you made a typo.

Copied directly from the webpage (correct):
> ln -s ~/palemoon/palemoon /usr/bin/palemoon

See the typo in your command? (Hint: It's near 'usr')
It's something we have all done...once. Many of us learned this way, too. Welcome to the club!

---

### Post by DVD-R on 2022-11-21
Sorry the typo I made was actually here.
I did have the command syntax correct - however I also added the . because the first palemoon directory under /user/ is a hidden directory.
Perhaps I shouldn't have done that?

Anyway 
Let me fix the actual command:
ln -s ~/.palemoon/palemoon /usr/bin/palemoon
Then navigated with the terminal into the /home/user directory - and typed palemoon
System response:
palemoon: command not found

---

### Post by ian-weisser on 2022-11-21
> **DVD-R said:**
> 
ln -s ~/.palemoon/palemoon /usr/bin/palemoon
Then navigated with the terminal into the /home/user directory - and typed palemoon
System response:
palemoon: command not found

Please show us the complete output of  the following three commands:
```

[FONT=courier new]ls -lah /usr/bin | grep palemoon
ls -lah ~/.palemoon/palemoon
echo $PATH[/FONT]

```

---

### Post by DVD-R on 2022-11-21
I think I figured it out.
The link needs to include the actual binary file which is to be executed - and that was not included because of the way I created the hidden directory.

I discovered a symbolic link to the whole palemoon directory within the usr/bin folder
I deleted that and then created the link this way:

ln -s /home/user/.palemoon/palemoon/palemoon /usr/bin/

Now when I navigate with the terminal in the /home/user directory - I can type palemoon and the application will execute.
So if I'm not mistaken - I would say I created a symbolic link to the palemoon executable file.

---

### Post by ian-weisser on 2022-11-21
You got it!

Congratulations!

You earned a celebratory cupcake.

---

### Post by DVD-R on 2022-11-22
ls -lah /usr/bin | grep palemoon:
lrwxrwxrwx  1 root root       38 Nov 21 21:07 palemoon -> /home/user/.palemoon/palemoon/palemoon

ls -lah ~/.palemoon/palemoon

total 56M
drwxr-xr-x 7 user user 4.0K Nov 27  2014 .
drwxrwxr-x 3 user user 4.0K Nov 21 12:48 ..
-rw-r--r-- 1 user user  467 Nov 27  2014 application.ini
drwxr-xr-x 7 user user 4.0K Nov 27  2014 browser
-rw-r--r-- 1 user user   40 Nov 27  2014 chrome.manifest
drwxr-xr-x 2 user user 4.0K Nov 27  2014 components
drwxr-xr-x 3 user user 4.0K Nov 27  2014 defaults
-rw-r--r-- 1 user user  127 Nov 27  2014 dependentlibs.list
drwxr-xr-x 2 user user 4.0K Nov 27  2014 dictionaries
drwxr-xr-x 3 user user 4.0K Nov 27  2014 distribution
-rw-r--r-- 1 user user  899 Nov 27  2014 libfreebl3.chk
-rwxr-xr-x 1 user user 381K Nov 27  2014 libfreebl3.so
-rwxr-xr-x 1 user user 7.3K Nov 27  2014 libmozalloc.so
-rwxr-xr-x 1 user user 936K Nov 27  2014 libmozsqlite3.so
-rwxr-xr-x 1 user user 252K Nov 27  2014 libnspr4.so
-rwxr-xr-x 1 user user 890K Nov 27  2014 libnss3.so
-rwxr-xr-x 1 user user 434K Nov 27  2014 libnssckbi.so
-rw-r--r-- 1 user user  899 Nov 27  2014 libnssdbm3.chk
-rwxr-xr-x 1 user user 111K Nov 27  2014 libnssdbm3.so
-rwxr-xr-x 1 user user 126K Nov 27  2014 libnssutil3.so
-rwxr-xr-x 1 user user  16K Nov 27  2014 libplc4.so
-rwxr-xr-x 1 user user  11K Nov 27  2014 libplds4.so
-rwxr-xr-x 1 user user 121K Nov 27  2014 libsmime3.so
-rw-r--r-- 1 user user  899 Nov 27  2014 libsoftokn3.chk
-rwxr-xr-x 1 user user 201K Nov 27  2014 libsoftokn3.so
-rwxr-xr-x 1 user user 197K Nov 27  2014 libssl3.so
-rwxr-xr-x 1 user user  45M Nov 27  2014 libxul.so
-rwxr-xr-x 1 user user 143K Nov 27  2014 mozilla-xremote-client
-rw-r--r-- 1 user user 6.3M Nov 27  2014 omni.ja
-rwxr-xr-x 1 user user 152K Nov 27  2014 palemoon
-rwxr-xr-x 1 user user 152K Nov 27  2014 palemoon-bin
-rw-r--r-- 1 user user   48 Nov 27  2014 platform.ini
-rwxr-xr-x 1 user user 132K Nov 27  2014 plugin-container
-rw-r--r-- 1 user user 2.0K Nov 27  2014 precomplete
-rw-r--r-- 1 user user  11K Nov 27  2014 removed-files
-rwxr-xr-x 1 user user 8.8K Nov 27  2014 run-mozilla.sh

echo $PATH:
/home/user/bin:/home/user/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin

---

### Post by DVD-R on 2022-11-22
I want to thank you ian-weisser for helping me through that!
Greatly appreciate!!!
You are awesome!  :-]

---

