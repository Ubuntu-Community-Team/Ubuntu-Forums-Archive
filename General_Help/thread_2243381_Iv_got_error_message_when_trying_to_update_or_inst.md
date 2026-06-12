---
title: "Iv got error message when trying to update or install."
date: 2014-09-08
forum: General Help
---

### Post by simon d w on 2014-09-08
man-db
 cups
 cups-bsd
E: Sub-process /usr/bin/dpkg returned an error code (1)

Wondering if somebody could help?  Thanks

---

### Post by Bashing-om on 2014-09-08
simon d w; Hi !

> 
Wondering if somebody could help? Thanks


We can sure try, and I think it a safe bet we can help. Words though out of context do not tell us much.
Post back the complete outputs - Between code tags - of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg -C

``` To see what the package manager has to releate.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by simon d w on 2014-09-08
```

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

```
 I get this after sudo apt-get update 

I've been working on this problem or ages now I've tried everything  from un-installing Software centre and Configure Printer programs. Each  time it just stalls, then when I look in Software centre i can see  packages half way installed. I've ran every script I can get my hands  on.  What is the command to find what the problem/error is?
It started when I accidentally rebooted half way through its original install 
```

  Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable) E: Unable to lock directory /var/lib/apt/lists/

```
  once I clear this problem it occurs again when I try and Install the printer.

---

### Post by nerdtron on 2014-09-08
Have you rebooted?
You can try to remove the lock using the answer on this post [http://askubuntu.com/questions/15433/unable-to-lock-the-administration-directory-var-lib-dpkg-is-another-process](http://askubuntu.com/questions/15433/unable-to-lock-the-administration-directory-var-lib-dpkg-is-another-process)

Then reboot, and then use the commands posted by Bashing-om

---

### Post by simon d w on 2014-09-08
Even when I reboot its still there.

---

### Post by nerdtron on 2014-09-08
Did you follow the link I gave you? do you still have errors after those commands? What are the errors?

From the link I gave you:
> [TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: answercell"]**This should be used as last resort. If you use this carelessly you  can end up with a broken system. Please try the other answers before  doing this.**

  You can delete the lock file with the following command:
  ```
sudo rm /var/lib/apt/lists/lock
```
  You may also need to delete the lock file in the cache directory
```
sudo rm /var/cache/apt/archives/lock
```

[/TD]
[/TR]
[/TABLE]


---

### Post by grahammechanical on 2014-09-08
> [COLOR=#000000]It started when I accidentally rebooted half way through its original install [/COLOR]

Perhaps the answer is a complete re-install of the distribution.

Regards.

---

### Post by Bashing-om on 2014-09-08
simon d w;
+1 on Grahams advise. Given the situation you have now, IF we can/do fix this I would never have complete confidence in the operating system.

Will be much faster and easier just to (RE-)install.
However, this can be a learning experience for all .. if you can afford and want to spend all the time and effort to fix this install .. you the man, your call.
I do look for it to be a messy fight.

[INDENT][INDENT]no scratches on my back
[INDENT][INDENT][INDENT]not one to run away from a fight
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by simon d w on 2014-09-08
Well I just ran the grub Ubuntu repair option on boot and asked it to fix all the options. Still not fixed the problem although it did something its booting faster, might have been another problem there.

---

### Post by simon d w on 2014-09-08
How do I purge all the drivers for the printer, it might be a semi installed bit that's causing it to not work? I could then start again.

---

### Post by simon d w on 2014-09-09
Ok so I solved the problem, ON MY OWN, I might add! As a Nubie I was well excited! 
  I found the driver name, on first installing, it asked you which  driver you want the Epson one the Ubuntu one or the Standard generic  driver. It comes up with its name before you press accept. 
  Then I remembered the terminal normally sorts stuff out or tells you what code to type or an error code to go and look for/ 
  You experts would probably say "well duh, obviously" but coming from windows you expect the graphical interfaces to work.  I typed 
  ```

sudo apt-get install epson-inkjet-printer-nx420

```
  Then went back in to Printer Configuration and selected my printer, which was showing up in a handy icon.

---

### Post by Bashing-om on 2014-09-09
simon d w; Hey hey !

You do good work, and do the forum a service by providing your solution.
And nope, there ain't no ""well duh, obviously" comments. We were all babes in the wood at one time. None of us were born knowing what we know.
And see, you taught me a thing or 2 in getting that proper driver installed.

And yes, this is linux  - NOT Windows - and it does require a different attitude and a different approach. Once beyond that point and click stage there is a learning curve to understand how the system functions;
"As a Nubie I was well excited! " you should be. Well done !

All over with now and not even any spilt milk"
Please mark this thread solved; 
aides others seeking the solution,
 helps keep the forum clean and
 precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
&&

[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT]

---

