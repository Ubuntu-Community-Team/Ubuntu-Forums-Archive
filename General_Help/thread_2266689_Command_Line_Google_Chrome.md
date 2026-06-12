---
title: "Command Line Google Chrome"
date: 2015-02-24
forum: General Help
---

### Post by grangemd-3 on 2015-02-24
I am trying to run google chrome from command line and I am able to however when i do this the command line won't let me run another command until i close this instance of google chrome.  Here is the output I get when i input google-chrome in terminal:


mgranger@Xubuntu-Server:~/Desktop$ google-chrome 
[26531:26531:0224/174814:ERROR:process_singleton_posix.cc(253)] readlink(/tmp/.com.google.Chrome.Teb1T6/SingletonCookie) failed: Permission denied
ATTENTION: default value of option force_s3tc_enable overridden by environment.
ATTENTION: option value of option force_s3tc_enable ignored.
[26573:26573:0224/174814:ERROR:sandbox_linux.cc(301)] InitializeSandbox() called with multiple threads in process gpu-process

Is there something i am doing wrong.  I would greatly appreciate any advice on this issue as i am trying to create a script to call up chrome and do a few other things however it hangs after i start chrome.

Thanks,
Matt

---

### Post by kerry_s on 2015-02-24
use: google-chrome --help
to see options available

---

### Post by nadarockyraccoon on 2015-02-25
If chrome is running the terminal instance will be occupied by that until chrome stops running. This is the same with any program run in terminal that does not automatically close after being run. If I can think of a way around this I'll let you know, but at the moment I'm drawing a blank.

---

### Post by Bucky Ball on 2015-02-25
Welcome. Yes, chrome occupies that terminal. If you want to run another command, open another terminal. ;)

Generally, if you're having problems with an app you'd open it via a terminal to help in troubleshooting. The terminal with give error messages, etc., when and if they occur to help you pinpoint what the issue might be. Not quite sure why you're opening it from a terminal. :-k

---

### Post by nadarockyraccoon on 2015-02-25
As it would be simply adding a space and an ampersand '&' after the command to call chrome should do the trick. This will open chrome and then allow for further command input so:
```
chrome &
next command
```
should work

---

### Post by Bucky Ball on 2015-02-25
> **nadarockyraccoon said:**
> As it would be simply adding a space and an ampersand '&' after the command to call chrome should do the trick. This will open chrome and then allow for further command input so:
```
chrome &
next command
```
should work

Thanks for the tip. ;)

I just tried that by opening VLC from a terminal and then typed 'top' in the same terminal. It worked! Ya learn something everyday.

---

### Post by mailfordannym on 2015-02-25
You can use chrome & next command or you can open another terminal.

---

### Post by oldos2er on 2015-02-25
Ctrl-z in terminal followed by **bg** will move the current process to the background. You'll still need to keep that terminal open.

---

