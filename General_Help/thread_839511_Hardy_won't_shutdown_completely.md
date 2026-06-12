---
title: "Hardy won't shutdown completely"
date: 2008-06-24
forum: General Help
---

### Post by d2843 on 2008-06-24
I have installed Hardy on two machines at home and it works great. However i just installed it on my dell dimension 9200 at work, and it won't shutdown properly. the progress bar progresses all the way and then just stays there. so all i see on my screen is the ubuntu logo with an empty progress bar until i do a hard shutdown. this happens every time.

---

### Post by ibuclaw on 2008-06-24
When you shutdown, press **Ctrl+Alt+F1** to display the shutdown messages, then write down the the last 3 or 4 lines that are displayed before the shutdown script hangs, and put them up in your next post.

For the moment instead of hard shutting down and potentially causing hard-drive damage, use the Magic SysRq keys to shutdown your PC safely.
```

Alt+Printscreen+R
Alt+Printscreen+E
Alt+Printscreen+I
Alt+Printscreen+S
Alt+Printscreen+U
Alt+Printscreen+O

```
Wait 2 seconds for each command to run and exit.

For info about the Magic SysRq functions, [read here.]("http://ubuntuforums.org/showthread.php?t=617349")

Regards
Iain

---

### Post by cszikszoy on 2008-06-24
Actually, you only need to press the keys in this order:
 
[hold alt the whole time]
sys-req
R
E
I
S
U
(B or O) B will reboot, O will shutdown

---

### Post by d2843 on 2008-06-24
i just discovered that this problem only occurs when i hit restart instead of shutdown.

when i press ctrl-alt-f1, it prints a few lines about NetworkManager and then the screen goes back to the ubuntu logo and blank progress bar.

i couldn't get that keyboard shortcut combination to work

unless someone can tell me how to fix this, i might just ignore it and only use the shutdown button. i don't want to keep doing hard shutdowns while i try different things.

---

### Post by clwhitt on 2008-08-26
> **d2843 said:**
> i just discovered that this problem only occurs when i hit restart instead of shutdown.

when i press ctrl-alt-f1, it prints a few lines about NetworkManager and then the screen goes back to the ubuntu logo and blank progress bar.

Did you ever resolve this problem?

I've been running Hardy for quite sometime with nary a problem. Then I installed it on a Dell Optiplex 745 for a friend, copied their Home directory files from another computer, and sure enough, I've run into the same problem.
There are no proprietary drivers and in all other respects, the computer runs great.

Chuck

---

### Post by d2843 on 2008-08-26
> **clwhitt said:**
> Did you ever resolve this problem?

no, i just stopped using restart.

---

### Post by mbeach on 2008-08-26
see post 4 at:
[http://ubuntuforums.org/showthread.php?t=796769](http://ubuntuforums.org/showthread.php?t=796769)

---

### Post by clwhitt on 2008-08-27
> **d2843 said:**
> no, i just stopped using restart.

A tip of the hat to mbeach for the link that led me to putting reboot=b in my /boot/grub/menu.lst file. This has done the trick (at least it has rebooted effortlessly for the last 5 reboots).

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9014ca3c-7e7c-444e-bbf3-556b276cfb02 ro quiet [COLOR="Red"]reboot=b[/COLOR] splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

A couple of questions: What does "reboot=b" do, and am I going to have to do this each time the kernel is updated?

Thanks again mbeach!

Chuck

---

### Post by mbeach on 2008-08-29
I believe if you add the reboot=b to the section of grub which is used for defaults (under the "default kernel options" under the "BEGIN AUTOMAGIC KERNELS LIST"), you should be ok.  What I'm not sure of though is if future kernels will require it.

don't hold me to the following, but I belive the reboot=b has something to do with telling the bios to handle/control the restart instead of the os or other hardware.

no problem, had the exact same issue, and had found the solution in these forums not so long ago.

---

### Post by doconnor on 2008-10-15
Does your hard drive shut down before you get the messages about NetworkManager?  

When I do a shutdown I get the Ubuntu screen and then my hard drive shuts down before I get the messages about NetworkManager.  I think this is the problem but I don't know how to stop the hard drive from shutting down prematurely.  I think the shutdown cannot access the hard drive and gives the NetworkManager messages.

I have spent hours searching and reading and tried some of the fixes without any luck.

In all my reading I have seen no mention of the hard drive shutting down.

Thanks,
Dale

---

### Post by esva on 2008-10-31
I didn't have this problem before but I do now with this 2.somethign.21 version of the kernel i think that came with the updates. i see some people had it with the .19 version, could it be that the kernel is incompatible with the hardware or bios or something like that? (i don't know of coputers) I mean now my keyboard is different (Numlock is not turned on and i can use it, I can't see to use the thingie that goes before hotmail.com)
 When I try to turn off my computer the exit message apears and the screengoes black but the messages of the daemons shutting off and whatever do not appear at all anymore. Just the screen goes black and the cpu doesn't turn off. I can't turn this off from xubuntu at all :(

---

### Post by clwhitt on 2008-11-01
Did you try the reboot=b fix? If not, look back before message #8 to see how to add this to your grub menu.lst.

---

### Post by Rodney9 on 2008-11-01
> **d2843 said:**
> I have installed Hardy on two machines at home and it works great. However i just installed it on my dell dimension 9200 at work, and it won't shutdown properly. the progress bar progresses all the way and then just stays there. so all i see on my screen is the ubuntu logo with an empty progress bar until i do a hard shutdown. this happens every time.

Same here with Ubuntu 8.10 64bit on a brand new PC built professionally with linux in mind. I have tried apm and a new install.

---

### Post by esva on 2008-11-01
yes but on the grub menu.lst thing . I think i read of domeone putting it in some weird place they didn't really give the path for and that i didn't know where it is so I dunno. I also tried reboot=h and s, cause i read it also, but it still doesn't work.
In the grub menu at the beginning it says ubutu x.xx.xx 21, ubuntu recover x.x.21, ubuntu x.x.19 and so on, so i tried the 19 one but it didn't work either.

I thought that the problem was the screen i use, cause i changed it, but i don't really think it is that, i think it's the updating i did like minutes after.
 I got in cd's in blank in the pc to burn my stuff and reinstall if anything failed , thinking that if I installed with the new screen it would fix itself, but for some reason it didn't recognize my cd's (that had nothing in them) so I am just not going that road yet.. very curious...

---

### Post by clwhitt on 2008-11-01
[COLOR="Red"]gksudo gedit /boot/grub/menu.lst
[/COLOR]
Scroll down toward the end until you see something similar to the below. Add "reboot=b" as indicated in the example, save the file and give it a try.

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=6b3a19dd-dc17-4a0a-addb-25c34f3552a6 ro quiet [COLOR="Red"]reboot=b[/COLOR] splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

---

### Post by esva on 2008-11-08
This is very embarassing but I dont remember what i did, but the computer does turn of now. I think the reboot =b didn't work, but reboot=h did, why, i dunno, At first they both id not work, but I think it because i had them in the wrong order, not i the end of line like in your example. I dunno if that is what worked though, cause when I turned on the pc the cnfigure screen thing apeared and after a few tries, i put other screens similar to mine, cause the samsung syncmaster753s was not available. For some reason this maybe worked. All  know is that at some day i turned it on and the pc was configured to 1024x768 ( as it is in windows) and the pc turned off. So I don't know exactly what did it. But it wasn't an update I think cause the updates were only for evince (the pdf thing) I guess it didn't turn off due to some inconsistencie it had in some line or something like that... Well I don't know of these things, that is obvious. thanks for the reboot=h in the last part of the line, cause maybe that was what did it for me.

---

