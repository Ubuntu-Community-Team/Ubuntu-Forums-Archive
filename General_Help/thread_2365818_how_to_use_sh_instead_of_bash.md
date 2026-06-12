---
title: "how to use sh instead of bash?"
date: 2017-07-11
forum: General Help
---

### Post by cedardoc on 2017-07-11
I need to troubleshoot a script for my android device.  Apparently non-rooted android phones use sh instead of bash (or busybox).  How do I enter sh terminal commands (on ubuntu) instead of bash?

Thanks, 
Dave

---

### Post by HermanAB on 2017-07-11
[herman@hack ~]$ sh
sh-4.2$

---

### Post by vocx on 2017-07-11
> **cedardoc said:**
> I need to troubleshoot a script for my android device.  Apparently non-rooted android phones use sh instead of bash (or busybox).  How do I enter sh terminal commands (on ubuntu) instead of bash?

Thanks, 
Dave
What exactly are you trying to do?

Maybe you are a bit confused. In most Linux systems, "/bin/sh" is not a program itself, but it is a link to "/bin/bash" (or to another shell such as Dash shell, Korn shell, Z shell, etc.). When a script is run with "/bin/sh", it actually calls Bash (or the other program), but in a compatibility mode in which it enters POSIX mode, and thus behaves like "sh". Some built-in commands behave slightly different in this mode.

[https://unix.stackexchange.com/questions/44836/when-sh-is-a-symlink-to-bash-or-dash-bash-limits-itself-to-posix-compliance-so](https://unix.stackexchange.com/questions/44836/when-sh-is-a-symlink-to-bash-or-dash-bash-limits-itself-to-posix-compliance-so)

It seems here that android actually uses a Korn shell "ksh"
[https://stackoverflow.com/questions/11950131/android-adb-shell-ash-or-ksh](https://stackoverflow.com/questions/11950131/android-adb-shell-ash-or-ksh)

Basically, as long as you don't use specific Bashisms, like name slicing and substitutions, double brackets [[ ]], etc., I think you should be fine with writing and testing your program in Bash, and running it with "/bin/sh ".

---

### Post by efflandt on 2017-07-11
As mentioned just type **sh** (Enter) in a terminal, which in Ubuntu typically runs **dash**. To for details about how that works, or what you may need to do differently than bash, see **man sh** which shows same as **man dash**.

To exit dash and return to bash, just hit Ctrl+D at the prompt (beginning of line).

---

### Post by cedardoc on 2017-07-11
I was trying to reproduce some calendar/date math from bash into a script on my phone, and because previous phones have been rooted, I assumed I had busybox on it, but unrooted phones don't.  I read they have just a straight "bourne shell", so I was trying to get that same environment on my ubuntu pc to do the testing there.

I'll include a screenshot from my phone. (just ignor the "warning:linker"warning" etc - that's just leftover from a failed attempt to get busybox on there without root.)

[https://www.dropbox.com/s/9siglf62ohqk8yb/Screenshot_20170711-095833.png?dl=0](https://www.dropbox.com/s/9siglf62ohqk8yb/Screenshot_20170711-095833.png?dl=0)

So if Vocx is correct, how do I test the various date commands as they would work in a korn shell? 

when I thought I needed busybox I just did this:
> busybox date -D "%s" -d "$(( today1 + today2 ))" +"%Y-%0m-%0d"

and that worked, but when I do this:
> david@GAx:~$ ksh date -d @"$(( today1 + $today2 ))" +"%B"
date: date: cannot execute [Exec format error]


that works on my phone, but not in ksh on ubuntu.

Any suggestions? (besides just plugging along entering code guesses on my phone, ha ha)

thanks, 
- Dave

---

### Post by cedardoc on 2017-07-12
Oops, ksh is probably different from mksh.  I'll try that tomorrow

---

### Post by steeldriver on 2017-07-12
If you want to run a string as a command, you need the -c flag:

```

$ ksh date
date: date: cannot execute [Exec format error]

$ ksh -c 'date'
Wed Jul 12 08:36:18 EDT 2017

```

or actually enter an interactive shell
```

$ ksh
$ date
Wed Jul 12 08:36:29 EDT 2017
$ exit

```

---

### Post by vocx on 2017-07-12
> **cedardoc said:**
> I was trying to reproduce some calendar/date math from bash into a script on my phone, and because previous phones have been rooted, I assumed I had busybox on it, but unrooted phones don't.  I read they have just a straight "bourne shell", so I was trying to get that same environment on my ubuntu pc to do the testing there.

I'll include a screenshot from my phone. (just ignor the "warning:linker"warning" etc - that's just leftover from a failed attempt to get busybox on there without root.)

[https://www.dropbox.com/s/9siglf62ohqk8yb/Screenshot_20170711-095833.png?dl=0](https://www.dropbox.com/s/9siglf62ohqk8yb/Screenshot_20170711-095833.png?dl=0)

So if Vocx is correct, how do I test the various date commands as they would work in a korn shell? 

when I thought I needed busybox I just did this:


and that worked, but when I do this:

that works on my phone, but not in ksh on ubuntu.

Any suggestions? (besides just plugging along entering code guesses on my phone, ha ha)

thanks, 
- Dave
First of all, you have a few misconceptions. Also the syntax of busybox is special.

Busybox includes many utilities that you find in a Linux distribution in a single executable. So, how does busybox know what program to call? Well, the busybox executable looks at its first argument, and then behaves like that program.
```

busybox date argument1 argument2

```
behaves as
```

date argument1 argument2

```

That syntax, "busybox program [options]", is specific to busybox, but is not normal for the regular shells (sh, bash, ksh, etc.).

In regular Linux systems, all programs are separate executable files, which normally live in "/bin" or "/usr/bin", or in any of the typical directories in the "$PATH" .

So, in a regular Linux distribution, you just call the program by its name, or its full name
```

date options
/bin/file options
/usr/bin/python options

```

You don't preface the program name with the shell, as you do in Android with Busybox
```

# wrong!
sh date
bash date
ksh date

```

What this does is it tries running a file "date" through the "sh", "bash", or "ksh" programs. Since the file "date" does not exist, or rather, since it is not a valid shell script, it fails with the "cannot execute" error.

In order to use a specific shell, first you explicitly start the shell, and then you call the appropriate programs, like in post #7.
```

sh
date -d @1512705804
exit

```

Also possible is to use the -c option of the "sh", "bash", or "ksh" programs to run whatever is enclosed in quotes with that shell
```

sh -c '[something here to run with sh]'
bash -c '[something here to run with bash]'
ksh -c '[something here to run with ksh]'

sh -c 'date -d @1511613131'

```

I just tested your code in my Ubuntu, running Bash, and it just works without problems. So, in my opinion you don't need to do anything special.
```

t1=1512705804
t2=183600
date -d @$(($t1 + $t2)) +%B
date -d @$(($t1 + $t2)) +%Y-%0m-%0d

```

The fact that you try running "ksh date" seems to be causing you problems, and as I mentioned earlier, you don't need to do that. You just need to run "date" directly.

For this very simple example, it should not matter if you are using "bash", "ksh", or "mksh", as it does not use anything special. It uses simple math $(()) and variable substitution $var, which is pretty standard now.

By the way, you don't need to quote "%B" or "%Y-%0m", etc., as these don't confuse the shell. You only need to escape the characters which actually affect the shell such as backslashes, parenthesis, or dollar signs in certain circumstances, or when you want to prevent names with spaces from breaking at the space. For this particular case, the percent symbol %, the plus symbol +, or the at @, are not special, they are just characters. The program "date" is the one actually taking these strings and interpreting what to do with them.

Remember that Busybox implements many programs in a Linux distribution, but it does not implement every option of every program. This means Busybox provides a subset of the functionality normally found in a desktop. If something works in your desktop computer, but does not work in Busybox, it may be that that functionality is not available. So, if you have errors, you should check whether the options you want are part of Busybox, or not [https://www.busybox.net/downloads/BusyBox.html](https://www.busybox.net/downloads/BusyBox.html) And this is independent of the shell. If the options are not in the Busybox program, a command may not work, whether you use "sh", "bash", "ksh" or another shell.

For example, it seems that Busybox only implements certain time formats for "date", and not the full set, as you would read in the desktop manual with "man date".

Hopefully you get a better idea how the shell works.

---

### Post by cedardoc on 2017-07-12
Thank you all so much, especially for [[COLOR=#DD4814][COLOR=#000000]voc[/COLOR][/COLOR][COLOR=#DD4814][COLOR=#000000]x[/COLOR][/COLOR]]("https://ubuntuforums.org/member.php?u=2054517")  for the needed explanation :)

As you can probably tell I'm not a computer guy by profession, so I usually just google, cut and paste and see what happens.  I should really learn Python (or so I hear) but bash (and now ksh etc) is just so awesome!!  They should teach it in elementary school...

---

### Post by vocx on 2017-07-12
> **cedardoc said:**
> Thank you all so much, especially for [[COLOR=#DD4814][COLOR=#000000]voc[/COLOR][/COLOR][COLOR=#DD4814][COLOR=#000000]x[/COLOR][/COLOR]]("https://ubuntuforums.org/member.php?u=2054517")  for the needed explanation :)

As you can probably tell I'm not a computer guy by profession, so I usually just google, cut and paste and see what happens.  I should really learn Python (or so I hear) but bash (and now ksh etc) is just so awesome!!  They should teach it in elementary school...
Yeah, copying and pasting is fine, but beware of that. Whenever possible you should try to learn what you are actually doing, because you don't want to stay ignorant forever. And mind you, without formal training, learning enough about computers may take you five to ten years or a lifetime. Things also change after many years, so keeping up to date is also important. Nobody likes the computer guy who hasn't learned anything new since the 1980s.

For Linux, having a working knowledge of Bash is great. Bash is like glue, it lets you write small scripts 10 to 30 lines long, basically just running things in sequence in a simple fashion. And most Linux distributions include Bash, or a similar shell like Dash, Ksh, etc., so your knowledge is quite portable. Python is better if you want to write longer programs, 50 to 200 lines of code or more, as it allows you to structure better your programs. But it's overboard for simple system management. Learning Bash is good if you use Linux, and learning Python (additionally) is good if you are pursuing an engineering career.

I don't think teaching Bash in elementary school would be such a great idea. With all the kids running around, they barely can concentrate on a topic. Now, secondary school, 17 or 18 year old students, before entering the workforce, or university, sure, they could use some Linux management classes!

---

### Post by cedardoc on 2017-07-13
Thought I should update that I found the solution:  

I installed** android-tools-adb**, plugged in my phone, and at the Ubuntu terminal typed in "adb shell" and voila!  I was basically at the terminal on my phone with a full keyboard.

I'd tried sh, dash, ksh, mksh and ash and non of them gave me the same results as the android terminal.  E.g. 

> david@GAx:~$ adb shell
hero2ltebmc:/ $ date -D "2017-07-13" +%s
1499986350


... only works with adb shell, but all of the above shells otherwise put up errors.

anyway, thanks again,
- Dave

---

### Post by vocx on 2017-07-14
> **cedardoc said:**
> Thought I should update that I found the solution:  

I installed** android-tools-adb**, plugged in my phone, and at the Ubuntu terminal typed in "adb shell" and voila!  I was basically at the terminal on my phone with a full keyboard.

I'd tried sh, dash, ksh, mksh and ash and non of them gave me the same results as the android terminal.  E.g. 



... only works with adb shell, but all of the above shells otherwise put up errors.

anyway, thanks again,
- Dave
Oh, right. Adb is the proper way to interface with your Android device. You can do nifty things, like take pictures, record a video of the screen, upload and download files to and from the phone, install packages, and stuff, all from your computer keyboard, just type "adb help".

By the way, the fact that "date -D" works with "adb" means the syntax of the "date" command in the Android phone is different from the the syntax of "date" available in the desktop computer. It does not mean that the actual shell is different. The shell could be the same, but if the "date" command is different it could take a different set of options, as it appears to be the case. Perhaps this is explained in the Android documentation, but I don't know where that would be.

Basically, the shell (either bash, ksh, mksh, dash, etc.) provides the basic rules of syntax of variable expansion, and some control structures like "for" and "if", while the individual programs, all those inside "/bin", have their own syntax. So, please try to realize that the shell is not the one controlling which options a program (such as "date") accepts, but it is the individual programs the ones controlling the options. So, this is probably the case that you saw here, with all shells you got errors, not because you had the wrong shell, but because you had the wrong "date" program. In your desktop you have one version (the GNU version actually), and in your phone you have another version (Android version?).

In modern Linux distributions, many small utilities like "date" are standardized, which means they follow the same rules, and behave the same way in different systems. In the past (1980s or 1990s), however, there were different programs which happened to have the same name, but actually were different in their behavior. So, at that time, the Unix users really needed to know which version (MIT date, GNU date, IBM date, etc.) they were using because using one command in one system would not work in another system. This problem is not as marked now, but occasionally happens if you are a hardcore system administrator and you need to deal with different or old systems.

In fairness, it is not very clear in your initial post what you wanted to do. However, I think your understanding of Android and the shell improved while you were researching this issue so that's good. Great that you found your solution.

---

### Post by cedardoc on 2017-07-14
Yes, now that you explain it that way I see I should have figured out that's what was happening from previous info in this thread.  Thanks for your patience and explanations - it was definitely helpful!

---

