---
title: "Touchscreen gateway cx210x configuration"
date: 2012-11-01
forum: General Help
---

### Post by Hollinheadk on 2012-11-01
I recently purchased a gateway cx210x, it came to me with ubuntu 12.04 as the OS. I have been trying to get the tablet portion of this computer to work but for some reason the calibrate touchscreen application gives me an error telling me that, there is no calibratible device found.
CAN ANYONE HELP ME WITH THIS ISSUE, this is my first experience with ubuntu so please keep it in lamens....
THANKS!!!!

---

### Post by Favux on 2012-11-01
Hi Hollinheadk,

Welcome to Ubuntu forums!


Does the digitizer (stylus) work at all?

---

### Post by Hollinheadk on 2012-11-01
hello Favux,
unfortunately no, the stylus doesn't work...
Thanks for the welcome!!

---

### Post by Hollinheadk on 2012-11-02
also just some added info, I have double checked that utouch and xinput are installed and up to date. I really don't know what else to do, my knowledge with windows products tells me that there may be a hardware issue or possibly a driver missing, but since I am a newbie to ubuntu I don't even know if that makes sense!!!

---

### Post by Favux on 2012-11-02
Alright.  I think it should be a serial tablet PC.  Open a terminal and run this command.
```
lsusb
```
If no tablet shows up in the list usb output then it likely is serial.

Then let's see if the digitizer is on a serial port and which one.  In the terminal run this command.
```
sudo dmesg | grep ttyS
```
And please post the outputs of the above two commands.

If we get the port then lets try to determine if there is output on that port i.e. does the digitizer work?  Run this command:
```
xxd /dev/ttySX
```
Where X is the number of the serial port.

xxd (hidrawX hexdump) will exit for devices not listed, otherwise CTRL and C to quit.  Bring the pen to the screen and move it around.  You know you have the right ttyS* when you see a reaction with an output of characters.


The driver is probably the fpit driver.  That was last worked on by a Xorg guru about a year ago.  After he got it cleaned up and building correctly he announced that support was being stopped but he would update it if users contributed tested code.

Unfortunately we've tried a couple of times to set up fpit serial tablet PCs without luck.  It could be the code doesn't support that.  The developer may have inadvertently broken it for serial tablet PCs because he didn't have any testers to give him feedback.  Or we might have messed up the setup.  I don't think either of the two users were very advanced.

I did write up some tablet PC .conf files for the fpit driver but the Xorg developer wouldn't take them unless they were tested and worked.  Which makes sense of course.  I still have them around somewhere I think.

---

### Post by Hollinheadk on 2012-11-02
ok ran the first command and got this
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ran the second command you advised and this was the response

Usage:
 dmesg [options]

Options:
 -C, --clear                 clear the kernel ring buffer
 -c, --read-clear            read and clear all messages
 -D, --console-off           disable printing messages to console
 -d, --show-delta            show time delta between printed messages
 -E, --console-on            enable printing messages to console
 -f, --facility <list>       restrict output to defined facilities
 -h, --help                  display this help and exit
 -k, --kernel                display kernel messages
 -l, --level <list>          restrict output to defined levels
 -n, --console-level <level> set level of messages printed to console
 -r, --raw                   print the raw message buffer
 -s, --buffer-size <size>    buffer size to query the kernel ring buffer
 -T, --ctime                 show human readable timestamp (could be 
                             inaccurate if you have used SUSPEND/RESUME)
 -t, --notime                don't print messages timestamp
 -u, --userspace             display userspace messages
 -V, --version               output version information and exit
 -x, --decode                decode facility and level to readable string

Supported log facilities:
    kern - kernel messages
    user - random user-level messages
    mail - mail system
  daemon - system daemons
    auth - security/authorization messages
  syslog - messages generated internally by syslogd
     lpr - line printer subsystem
    news - network news subsystem

Supported log levels (priorities):
   emerg - system is unusable
   alert - action must be taken immediately
    crit - critical conditions
     err - error conditions
    warn - warning conditions
  notice - normal but significant condition
    info - informational
   debug - debug-level messages

---

### Post by Favux on 2012-11-02
I assume you garbled **sudo dmesg | grep ttyS**.  That's the output you get when you haven't entered a command correctly but at least dmesg was recognized as the command you were attempting to use.  Try again.  It should ask you for the password.  Just copy and paste.

---

### Post by Hollinheadk on 2012-11-02
when I copy and paste I get no response...

---

### Post by Hollinheadk on 2012-11-02
but, I don't know if this helps when I do** sudo dmesg **it gives a very long description of everything on the computer, or at least I think that is what it is...

---

### Post by Favux on 2012-11-02
Right that's the output on dmesg's ring buffer.  It's big but not endless and so newer stuff starts over writing older stuff, hence ring.  That's why we are using the grep command to just pick out anything to do with serial ports or ttyS.

Alright try just:
```
dmesg | grep ttyS
```

If still nothing that is puzzling.  We do need to figure out the port.  I wonder if setserial needs to be installed or what.  What do you see when you run:
```
setserial -g /dev/ttyS*
```

By the way I just realized we might be able to use input-attach instead of fpit.  That would avoid the fpit problems if it worked.

---

### Post by Hollinheadk on 2012-11-02
ok ran the first command and still got nothing, ran the **setserial **command and it told me that setserial needed to be installed so I installed it then re entered the second command and got a long list starting with **/dev/ttyS0:** ending in **/dev/ttySL0 **all of them saying permission denied

---

### Post by Favux on 2012-11-02
Did you reboot?  See installing setserial is one of the trip points.  I'm not sure if that is required anymore and if installing it messes things up.  It shouldn't, it is suppose to auto-configure.  But the Gateways have always been touchy.  Some set up easy and others required some voodoo.

Ok that means it want you to be root, i.e. sudo so try the first one then:
```
sudo setserial -g /dev/ttyS*
```

What we are trying to do is avoid you having to run xxd against every serial port you see in the output of:
```
ls /dev/ttyS*
```
If you have to do it manually you have to.  Start at ttyS0 then ttyS1 etc.  Usually the port it is on isn't much higher than 5 to 8 or so.  Most often S0 or S1.

---

### Post by Hollinheadk on 2012-11-02
this was my response to the first command


/dev/ttyS0, UART: unknown, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS10, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS11, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS12, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS13, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS14, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS15, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS16, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS17, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS18, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS19, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS20, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS21, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS22, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS23, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS24, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS25, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS26, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS27, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS28, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS29, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3
/dev/ttyS30, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS31, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS4, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS5, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS6, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS7, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS8, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS9, UART: unknown, Port: 0x0000, IRQ: 0
Cannot get serial info: Invalid argument

---

### Post by Hollinheadk on 2012-11-02
to be quite honest I don't know if you want me to run the second command or if that is a command I am waiting to do when we find the port

---

### Post by Favux on 2012-11-02
Alright, it looks like you only need to look at 0 through 3.  If so 4 isn't bad.

Second command would also show you you have 32 ports, 0-31.

---

### Post by Hollinheadk on 2012-11-02
Not to sound like a complete idiot but how do I check the ports?

---

### Post by Hollinheadk on 2012-11-02
also ran the second command and it said  no such file or directory

---

### Post by Favux on 2012-11-02
That's the xxd command from earlier.  So X is 0 or 1 or 2 or 3 or 4.  See if the stylus gives you output.

By the way is your stylus one of the ones that requires a battery?  If so is the battery relatively fresh?

---

### Post by Hollinheadk on 2012-11-02
Ok well I ran the xxd command, on port 0 it asked me for my password I entered it and then it said

input/output error

then without prompting me for a password it said the same thing for ports 1-3

---

### Post by Favux on 2012-11-02
Sudo lasts for like 5 minutes before you have to reuse it.

So what does that mean?  There isn't going to be a Port: 0x0000, IRQ: 0.  With what we have it should be one of those four.  Let me see if I can dig up an old setserial line.

The problem is there used to be just 5 ports.  S0 to S4.  Then with Natty they changed something and suddenly there were 32.  And I haven't ever seen any documentation about what they did or why.  My guess is with Upstart they just built in enabling all possible ports.  Before that if you needed an extra port you could add it manually as a kernel parameter.  Maybe they worried if a user did that it would mess up the Upstart boot chain?

So is setserial not automatically configuring the port correctly or is your stylus battery dead?  A dead battery may be partly why it was sold.

Gateway didn't want the users to replace the battery.  It wanted you to pay them to do it.  So it glued the battery in.  See:  [http://www.youtube.com/watch?v=7yI-EJvR7IY](http://www.youtube.com/watch?v=7yI-EJvR7IY)  Instead of or in addition to the thread I wonder about heating with a hair drier to loosen the glue.  Don't think that would damage the circuit board if you wrapped the lower stylus barrel towards the tip where the board is with cloth as a heat shield.

---

### Post by Hollinheadk on 2012-11-02
also to answer the battery question, the stylus does have a battery but according to the gateway site the battery is irreplaceable so that leads me to believe that it is charged by placing it in its hole in the side of the laptop, although I guess the darn thing could be dead, am I safe to assume that me touching the screen will have no effect....

---

### Post by Favux on 2012-11-02
Right.  It has to be the stylus with a non-dead battery.

I guess I would look at the glue and see if I could slip one of my small Xacto blades up there to cut/pry it out.  Still might want to try the heat idea.

---

### Post by Hollinheadk on 2012-11-02
ok, so I will have to explore the battery issue tomorrow....

my only other concern is that the configure program is not recognizing a device to calibrate, so does that mean that my device (the screen) is damaged or would it be giving me that message because the battery is dead???

---

### Post by Favux on 2012-11-02
No that's because the digitizer can't respond with coordinates until it is configured and working.  Which hopefully we've partially done with setserial.  In other words have it on a serial port, even if we don't have anything yet to handle the raw input coming in over the port.

Unfortunately you only have Ubuntu on your tablet PC so you can't boot into Windows to test the stylus.  Not much chance you know someone with the same laptop where the digitizer is working with their stylus so you could check yours on it I suppose.

But at this stage we can't rule out that it has a bad digitizer.  Or say the internal serial connection has come loose or some such.

---

### Post by Hollinheadk on 2012-11-02
okay well being that its almost 2 am my time and we are pretty sure we narrowed down the issue, I will work out the battery problem tomorrow and go from there....

I appreciate all your help!!!

Off this subject: during my fiddling with this trying to get it to work I installed a couple programs from the command prompt and can't figure out how to remove them do you know how I could uninstall these??? the programs are engauge-digitizer and ktouch which to me both sounded like things that could fix my problem but in all actuality are no where near what was needed obviously...

---

### Post by Favux on 2012-11-02
Yes.  Unless you compiled them APT should have a record of them so you could uninstall them from the command line or use the Software Center or Synaptic Package Manager.

---

### Post by Hollinheadk on 2012-11-02
what would be the code for uninstalling from the command line, I attempted to uninstall from software center but it wouldn't let me but it does have a record.

---

### Post by Hollinheadk on 2012-11-02
nevermind I found synaptic pkg. mgr. and removed them from there..... Thanks again for all you help and if I have any other problems I will be back tomorrow!!!

---

