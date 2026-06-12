---
title: "How do I force a application shutdown"
date: 2023-03-22
forum: General Help
---

### Post by skywalker007 on 2023-03-22
Hi

The following has happened to me, I had a application running that appeared to crash and I could not even move the pointer or go to any other active screens. I know in windows I can press CTRL+ALT+DEL and then get a list off all applications where I could just go and do a force shutdown of that one or multiple applications so that I do not have to restart by using the power off button.

Is there a way to do a application force shutdown if the pointer does not work?

Thanks
Johan

---

### Post by TheFu on 2023-03-22
Switch to a different tty/ptty (<cntl><alt>-F1 thru F6 to switch), check the process table and send a TERM signal to that process.  There are lots of different signals that can be sent, but 99% of the time a SIGTERM will suffice.  For really stuck programs, the OS can get a signal to kill the program, use the SIGKILL signal.  The **kill** command is used.  The problem with kill is that it wants a PID - process ID, which we have to get using the **ps** command (or **top** or **htop**).  Let's say I've looked up the PID for firefox and it is 24347.
```
$ kill 24347
```
will send the "nice" shut-yourself-down signal and almost always works.  If it doesn't work, then I'd want to tell the OS to kill the firefox process ...
```
$ kill -9 24347
```.  That will bring it down.  Period.  Modern firefox runs a separate process for each tab, so to kill the main process which will kill all the child processes too, we need to find that specific PID. It is usually the lowest PID. Keep that in mind.  Every running process has a PID.

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) probably explains all of this more clearly.  For X/Windows programs, if the mouse still works, you can use **xkill** to point the skull at the specific window to kill, but if the mouse or GUI are frozen, you need to get to a tty/ptty.

Or you could ssh in from a remote system, assuming you have another box and already setup ssh on both.

---

### Post by mIk3_08 on 2023-03-23
> **skywalker007 said:**
> Hi

The following has happened to me, I had a application running that  appeared to crash and I could not even move the pointer or go to any  other active screens. I know in windows I can press CTRL+ALT+DEL and  then get a list off all applications where I could just go and do a  force shutdown of that one or multiple applications so that I do not  have to restart by using the power off button.

Is there a way to do a application force shutdown if the pointer does not work?

Thanks
Johan
I think if you can still run the system monitor you can  just then choose the apps process that is to be killed. Or you can just  run the command below in your terminal.
```
sudo pkill <application process>
```
Regards and cheers

---

### Post by DuckHook on 2023-03-23
> **skywalker007 said:**
> Hi

The following has happened to me, I had a application running that appeared to crash and I could not even move the pointer or go to any other active screens. I know in windows I can press CTRL+ALT+DEL and then get a list off all applications where I could just go and do a force shutdown of that one or multiple applications so that I do not have to restart by using the power off button.

Is there a way to do a application force shutdown if the pointer does not work?

Thanks
Johan
Please pay attention to TheFu's post. In Linux, killing a running process involves a multilayered approach. We try to use the most "elegant" method first because this leaves the system in the most stable state with the least risk to your data. It's only if the least disruptive method doesn't work that we take the next step to a more disruptive method. Each escalation means more risk to system stability and your data.

If nothing else works and you can't even switch tty/ptty, then use Sysrq before actually pulling the plug (forcing shutdown with power switch is the same as pulling the plug). Explanation of Sysrq: [https://en.m.wikipedia.org/wiki/System_request](https://en.m.wikipedia.org/wiki/System_request)

If you pull the plug, Linux does not have a chance to write all data from buffers to disk, which could leave you in a bad state when you boot up again. Using Sysrq allows the system to synchronize so that at least your file system is intact, although you will lose all unsaved work.

---

