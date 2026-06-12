---
title: "Shell scripts won't run - path variable issue?"
date: 2007-11-21
forum: General Help
---

### Post by LifeZagger on 2007-11-21
I have been researching this for hours, and I am totally clueless as to my problem...

I have a shell script I've saved as /share/scripts/webtrack2.sh

I've made the script executable, and I've changed my path so that /share/scripts is in my path.

I can only execute this script when I am in the /share/scripts directory.  Typing echo $PATH shows me:
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/share/scripts
```

Oddly (to me anyway), I can't execute this script from my root directory either by typing webtrack2.sh or /share/scripts/webtrack2.sh.  I would think at least one of those should work, but obviously I am wrong.

Is there something I am missing here??  I imagine there is something basic I am not understanding...

---

### Post by juantovarm on 2007-11-22
yes, you are missing something, the way to execute scripts: there are three ways to execute scripts, that i am aware of anyways, and i only remember 2, i have never used the other way:

1- while in the folder containing the script type: ./nameofscript (a period and a slash)
2- while in the folder of the scrip type: sh nameofscript

---

### Post by LifeZagger on 2007-11-22
Thanks for the quick reply.  Ultimately, I need to find out that third way!

I plan on running this script with cron, but I had problems trying to set that up - I'm thinking that problem is related to the fact that I can't run the script at all when I'm not in the directory of the script itself.

---

### Post by bingoUV on 2007-11-22
What do you mean by "can't run the script"? Does it give an error? Does it not behave as you expect it to? 

In the beginning of the script, do you have the guidance?
```

#!/bin/sh

```

---

### Post by banewman on 2007-11-22
All your addresses start /share... - shouldn't that be /usr/share?

---

### Post by LifeZagger on 2007-11-22
> **bingoUV said:**
> What do you mean by "can't run the script"? Does it give an error? Does it not behave as you expect it to? 

In the beginning of the script, do you have the guidance?
```

#!/bin/sh

```

Yes, it would make sense for me to tell you what I DO get, eh?  I try to run the script and I get:
cat: list.txt: No such file or directory

---

### Post by LifeZagger on 2007-11-22
> **banewman said:**
> All your addresses start /share... - shouldn't that be /usr/share?

I mapped one of my hard drive partitions as /share from the root directory - so in this case it is correct.

I am still more or less a linux novice, so perhaps I am making a directory or path design mistake here....

---

### Post by banewman on 2007-11-22
Open nautilus and navigate to the root directory - should start with folders bin, boot etc - browse through there to find one that is your share folder. If you have to open a folder to find it you need to add that to your path. :)

---

### Post by LifeZagger on 2007-11-22
> **banewman said:**
> Open nautilus and navigate to the root directory - should start with folders bin, boot etc - browse through there to find one that is your share folder. If you have to open a folder to find it you need to add that to your path. :)

I see what you are saying.  /share is a subdirectory of my root directory, so my path is legitimate.  Could permissions on that directory be an issue?

If this matters at all, I am using Kubuntu - hopefully that isn't the cause of my issue!

---

### Post by banewman on 2007-11-22
When you typed "echo $path" the first file starts /usr...
open your file browser to manually check where the "share" folder you created lives.
If it is not in /usr then why did that show when you typed "echo $path" ? :)

---

### Post by Linteg on 2007-11-22
> **LifeZagger said:**
> Yes, it would make sense for me to tell you what I DO get, eh?  I try to run the script and I get:
cat: list.txt: No such file or directory
Are you trying to open a file with a relative address in the script? If so, it is probably relative to the location where you are when you execute the script, and not to where the script is located.
For example, you would have to change cat file.txt | grep a to cat /share/scripts/file.txt | grep a.

---

### Post by bingoUV on 2007-11-22
Problem is inside the script. Not the location, not the permissions, not the PATH; but the code.

If you access any file, give its full path. You seem to be "cat"-ting a file without giving full path. Review your entire script, and correct all such usages of files.


---

### Post by LifeZagger on 2007-11-22
> **Linteg said:**
> Are you trying to open a file with a relative address in the script? If so, it is probably relative to the location where you are when you execute the script, and not to where the script is located.
For example, you would have to change cat file.txt | grep a to cat /share/scripts/file.txt | grep a.

How entirely obvious once you point it out.  I didn't understand what the error was, but now it seems I should have figured it out.  I'll chalk it up to learning linux!  Let's see if i can get it to run now.

Thanks!

---

### Post by LifeZagger on 2007-11-22
> **bingoUV said:**
> Problem is inside the script. Not the location, not the permissions, not the PATH; but the code.

If you access any file, give its full path. You seem to be "cat"-ting a file without giving full path. Review your entire script, and correct all such usages of files.

It worked!  Hours and hours of me trying to figure this out, never quite getting the point!  

Thanks!

---

