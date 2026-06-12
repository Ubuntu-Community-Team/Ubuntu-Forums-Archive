---
title: "why my disk got full?"
date: 2024-11-01
forum: General Help
---

### Post by ronjjjg8885 on 2024-11-01
here is a screen shot?

what to do?

tnx

---

### Post by Paddy Landau on 2024-11-01
Taken from [this answer]("https://askubuntu.com/a/747022/2088"):

Your system has some sort of repeating error, and this is being logged in syslog.

To find out what the error might be, enter this command in a terminal:
```
tail --lines=100 /var/log/syslog
```
Post the results here if you don't understand them.

To clear your current syslog, enter this command in a terminal:
```
sudo truncate --size=0 /var/log/syslog
```
This is only a temporary solution, because we need to find out why it's being filled.

---

### Post by ronjjjg8885 on 2024-11-01
thank you
i will try.. it is hard to type on that computer because it is a media center without a proper keyboard..
the only keyboard i've there now is a problematic remote control..

i will have to take my main computer keyboard and connect it on the media center computer....
i will do it..

---

### Post by ronjjjg8885 on 2024-11-01
i have entered both commands

here is the paste..
[https://pastebin.com/tMQz36Sp](https://pastebin.com/tMQz36Sp)

---

### Post by TheFu on 2024-11-01
A few months ago, we helped someone else here figure out all the ways file systems can fill up.  Please find that thread, since there are lots of good tools and techniques shown.

And please don't post images inline, especially when 1500 text characters can easily show the same information and allow people to copy/paste important parts in their replies.  Make it easy to help you, please.

---

### Post by Paddy Landau on 2024-11-01
> **ronjjjg8885 said:**
> here is the paste…
Thank you.

This looks like an [old bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1857392"), also mentioned in a [previous thread]("https://ubuntuforums.org/showthread.php?t=2458075").

Look at this [Reddit thread]("https://redd.it/yzkg3x") and at comment #13 in the above-mentioned bug report.

Does any of that help?

---

### Post by ronjjjg8885 on 2024-11-01
too complicated.

the second command that you gave me will not solve it for good?

---

### Post by deadflowr on 2024-11-01
What command?
Do you mean the truncate command in post #2?
I thought he wrote it's temporary.
Basically, it should allow you some breathing room until you find a real fix.

Did you look at the suggestion in post #6?

You can run these commands
```
gsettings set org.gnome.shell.extensions.dash-to-dock hot-keys false

gsettings set org.gnome.shell.extensions.dash-to-dock hotkeys-overlay false

gsettings set org.gnome.shell.extensions.dash-to-dock hotkeys-show-dock false
```

These command are the same as what would be done with dconf-editor.
Only difference is dconf-editor is a nice gui app.

---

### Post by TheFu on 2024-11-01
> **ronjjjg8885 said:**
> too complicated.

the second command that you gave me will not solve it for good?

Sometimes there are 10,000 possible causes for an issue, so you need to help yourself to figure out the problem.  Deleting logs should happen automatically. For a system running fine, that's what happens. Something has gone wrong with YOUR system.  Until you figure out what has gone wrong, there won't be any permanent solution possible.  

Removing logs faster just masks the problem. If not addressed, that problem WILL get worse and worse and worse, until the system won't boot at all.


But fixing it or not is 100% your choice.

---

### Post by dragonfly41 on 2024-11-01
A sticking plaster is to install Stacer (Linux monitoring tool) and third button down is a Cleaner which can delete all or some logs. Until you can get a grip on why? Stacer gives you a dashboard into the Ubuntu engine room.

---

### Post by ronjjjg8885 on 2024-11-01
what will happen if i make a new fresh installation of ubuntu or perhaps even mint?

can't really believe linux is so buggy..

tnx for the clarifications

---

### Post by TheFu on 2024-11-01
> **ronjjjg8885 said:**
> what will happen if i make a new fresh installation of ubuntu or perhaps even mint?

can't really believe linux is so buggy..

tnx for the clarifications

This isn't a bug. It is a feature.  You are being told that something is wrong, please fix it.  

Let me try an analogy.  Ignoring a leaky roof doesn't make the leak stop. If you can't fix the leaking roof yourself, then call a roofer in for a patch over the hole before it gets worse.  For small holes in the roof, a little patch is easy.  Wait longer and it gets worse. This should be obvious.

If the issue is with the hardware, doing a fresh install won't change anything, assuming you didn't do something to cause the issue directly. However, you might have done something by accident to cause the problem.  At this point, nobody knows.

Without looking at the logs, nobody knows what the problem is.  You want a definitive answer, but won't look at it yourself or allow a roofer to look at it.  Leaks never get better over time.  If addressed quickly, a tiny leak never gets worse and it is easy to correct.   

See how this is analogous to looking at your logs?   It could be warning you that your CPU or GPU is over heating or that a HDD is failing - or it could be that someone is trying to hack your system - or it could be that something which needs to be configured hasn't been configured yet.  We don't know.

Please take a look at your system log files. That's step 1.

If you don't want to do that, perhaps another OS would be a better choice.  I hope you check the oil and tire pressure in your car sometimes. All non-trivial things need a little maintenance from time to time.

---

### Post by Paddy Landau on 2024-11-02
> **ronjjjg8885 said:**
> what will happen if i make a new fresh installation of ubuntu or perhaps even mint?
If this is a hardware problem, changing your distribution will do nothing.
> **ronjjjg8885 said:**
> can't really believe linux is so buggy.
If you use hardware that is Linux-compatible, you won't have this sort of problem. It's the same if you try to use Windows or MacOS on a device that's not compatible with them.

Try the fix that deadflowr gave you; see if that works.

---

### Post by ronjjjg8885 on 2024-11-02
i see
thanks.
i don't know if i can succeed with the instructions....

i've been told in the past the a computer that doesn't support linux is very rare.....

i think it is a good idea to mention that it can be not compatible before people download linux.. because it is important to be honest with ourselves and others.....

---

### Post by Paddy Landau on 2024-11-02
> **ronjjjg8885 said:**
> i don't know if i can succeed with the instructions.
Just enter the commands that you were given in the terminal.
> **ronjjjg8885 said:**
> i've been told in the past the a computer that doesn't support linux is very rare.
It's not that rare. But, Canonical does have a list of certified devices. Also, if you want to buy a Linux-compatible computer, some hardware vendors explicitly support Linux. For example, Dell and Lenovo (not all devices; only some of them); System76; and others.
> **ronjjjg8885 said:**
> i think it is a good idea to mention that it can be not compatible before people download linux.. because it is important to be honest with ourselves and others.
No one is being dishonest. A computer sold with Windows is compatible with Windows. A computer sold with Linux is compatible with Linux. A computer sold with MacOS is compatible with MacOS. And so on.

Anyway, your computer is probably fine as long as you solve this problem. Enter the commands that deadflowr gave you, and tell us what happens.

---

### Post by ronjjjg8885 on 2024-11-02
i will try it later.
thank you very much......

---

### Post by TheFu on 2024-11-02
> **ronjjjg8885 said:**
> 
i've been told in the past the a computer that doesn't support linux is very rare.....

i think it is a good idea to mention that it can be not compatible before people download linux.. because it is important to be honest with ourselves and others.....

There's a difference between "supported" and "made to work".  Nearly all computers can be "made to work" with Linux.  There are a few exceptions, but whether any computer can be made to work with linux or not is dependent on many considerations, including the skills and endurance of the person making the attempt.  

The list that is "supported" is tiny.  I've never owned an explicitly "supported" Linux Computer.

If you want a computer to "just work", go buy a Mac.  Apple makes both the OS and hardware. There is no competition. Enjoy whatever capabilities Apple has decided you need. Don't expect great flexibility and random hardware peripherals to work. Expect to pay 2-3x more for almost everything related to that computer.  Apple does great engineering and they stand behind their product, which is why they are so very costly.

Have you read any license agreement for any software?  Most have a clear statement that the software isn't guaranteed for any particular use.  Doesn't matter if it is GPL, LGPL, Apple or Microsoft creating the license.

Here's the relevant GPLv3 section:

>   15. Disclaimer of Warranty.

  THERE IS NO WARRANTY FOR THE PROGRAM, TO THE EXTENT PERMITTED BY
APPLICABLE LAW.  EXCEPT WHEN OTHERWISE STATED IN WRITING THE COPYRIGHT
HOLDERS AND/OR OTHER PARTIES PROVIDE [B]THE PROGRAM "AS IS" WITHOUT WARRANTY
OF ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING, BUT NOT LIMITED TO,
THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR
PURPOSE.[/B]  THE ENTIRE RISK AS TO THE QUALITY AND PERFORMANCE OF THE PROGRAM
IS WITH YOU.  SHOULD THE PROGRAM PROVE DEFECTIVE, YOU ASSUME THE COST OF
ALL NECESSARY SERVICING, REPAIR OR CORRECTION.

That's pretty standard in all software licenses.

Here's the relevant BSD license section:
> THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS “AS IS” AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND **FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED.** IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

You agree to these if you use software with these licenses.

Here's the relevant Microsoft license section:
>  12. DISCLAIMER OF WARRANTY.The software is licensed “as-is.” You bear the risk of using it. Microsoft gives no express warranties, guarantees or conditions. You may have additional consumer rights under your local laws which this agreement cannot change. To the extent permitted under your local laws, **Microsoft excludes the implied warranties of merchantability, fitness for a particular purpose** and non-infringement.
[https://support.microsoft.com/en-us/windows/microsoft-software-license-terms-e26eedad-97a2-5250-2670-aad156b654bd](https://support.microsoft.com/en-us/windows/microsoft-software-license-terms-e26eedad-97a2-5250-2670-aad156b654bd)

I can't recall ever seeing any software license that didn't have a similar clause.  That's life.  OTOH, the BSD and GPL licenses provide some great terms to ensure we can use, modify, and share the software with anyone, though their are a few limitations.

---

### Post by ronjjjg8885 on 2024-11-02
do you mean these commands?
> gsettings set org.gnome.shell.extensions.dash-to-dock hot-keys false

gsettings set org.gnome.shell.extensions.dash-to-dock hotkeys-overlay false

gsettings set org.gnome.shell.extensions.dash-to-dock hotkeys-show-dock false

or you mean that i need to re visit the links that you gave me to look for the commands there?

---

### Post by deadflowr on 2024-11-02
> **ronjjjg8885 said:**
> do you mean these commands?
```
gsettings set org.gnome.shell.extensions.dash-to-dock hot-keys false

gsettings set org.gnome.shell.extensions.dash-to-dock hotkeys-overlay false

gsettings set org.gnome.shell.extensions.dash-to-dock hotkeys-show-dock false
```

or you mean that i need to re visit the links that you gave me to look for the commands there?

Those commands do the same thing as what you would do with the dconf-editor as described in the links.
All I've done is posted the command line commands.

Seemed quicker than having to install dconf-editor and then learn how to navigate it to the section you need to be in to do that.

Whether or not you revisit the links is up to you.

---

### Post by ronjjjg8885 on 2024-11-02
ok
that's it? i don't need to make anything else? just these 3 commands? how can i check that it is ok now?

---

### Post by deadflowr on 2024-11-02
> **ronjjjg8885 said:**
> ok
that's it? i don't need to make anything else? just these 3 commands? how can i check that it is ok now?
Sure, if you ran the commands or installed dconf-editor and followed the advice in the links.
That should be all that you needed to do.

Note that all it is is a possible solution.
No guarantee that it will work.
All we know is that it's helped other with the same issue.

You can just recheck your logs again.
And see if it still spams those repeating entries.

Edit:
Run the tail command again, since all the new entries will be at the end of the log anyway.
```
tail /var/log/syslog
```
I doubt you'll need to see more than the last 10 lines, which the tail command outputs without needing to add the --lines option.

---

### Post by yancek on 2024-11-02
Have you had this problem since you first installed 24.04?  If not, what did you change just prior to this happening.  Syslog files will fill when users are messing with software and configuration file when not understanding what they are doing.  You should delete the syslog file as it will be recreated when any information need to be logged.  I don't believe I've ever seen a 200+GB log file before.

---

### Post by ronjjjg8885 on 2024-11-04
the change i've made is to install chromium and an extension that makes missile alerts.. since then i've removed both because i've found a better way to get the alerts..

i'm waiting to get the keyboard i've ordered and to be able to enter commands more easily on the media center computer....

i will let you know when i proceed with that..

thank you

edit..
no.. i didn't had the problem when in installed ubuntu....

---

### Post by dragonfly41 on 2024-11-04
Explore RabbitMQ for alerts ..

---

