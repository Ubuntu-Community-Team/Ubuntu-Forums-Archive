---
title: "Error, Unable to resolve host (name of laptop)"
date: 2023-11-14
forum: General Help
---

### Post by Advait on 2023-11-14
Here's the error. How to fix? 22.04.3. "advait-Bravo-15-A4DDR" is the name of my laptop. I'm a newb (know nothing about command line) so kindly respond appropriately. I can copy and past commands.

```
advait@advait-Bravo-15-A4DDR:~$ sudo apt list &#8211;-installed
sudo: unable to resolve host advait-Bravo-15-A4DDR: Name or service not known
[sudo] password for advait: 
Listing... Error!
E: input:0-13: error: Expected pattern
   &#8211;-installed
   ^^^^^^^^^^^^^
advait@advait-Bravo-15-A4DDR:~$ sudo apt list &#8211;-installed
sudo: unable to resolve host advait-Bravo-15-A4DDR: Name or service not known
Listing... Error!
E: input:0-13: error: Expected pattern
   &#8211;-installed
   ^^^^^^^^^^^^^
advait@advait-Bravo-15-A4DDR:~$ sudo apt show foxit
sudo: unable to resolve host advait-Bravo-15-A4DDR: Name or service not known
N: Unable to locate package foxit
N: Unable to locate package foxit
E: No packages found
advait@advait-Bravo-15-A4DDR:~$ 

```

---

### Post by #&amp;thj^% on 2023-11-14
Please check and show us:
```
 hostname
lvm-ThinkPad-X1-Carbon-7th
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> cat /etc/hostname 
lvm-ThinkPad-X1-Carbon-7th

```
The same hostname should be listed in the /etc/hosts file as well.

---

### Post by MAFoElffen on 2023-11-14
@Advait --

Just to be clear... We have worked with you before, so can assume a few things... Like I know you do not spend much time in a Terminal session... But do seem to spend a lot of time online, from a browser right?

We need to ask you questions to clarify what is happening, and narrow the search path of what to suspect.

Where exactly are you seeing this error, and what exactly is the error?

Because knowing you spend a lot of time researching and learning things by surfing the web, was the error along the lines similar to:
> 
*"Unable to resolve host no address associated with hostname&#8221;*

While trying to load a webpage in a browser? That would imply a problem with either DNS or the website... A networking issue would be suspected.

Or was it something you saw on the splash screen while you were booting? That would be the computer hostname.

---

### Post by Advait on 2023-11-14
> **MAFoElffen said:**
> @Advait --

Just to be clear... We have worked with you before, so can assume a few things... Like I know you do not spend much time in a Terminal session... But do seem to spend a lot of time online, from a browser right?

We need to ask you questions to clarify what is happening, and narrow the search path of what to suspect.

Where exactly are you seeing this error, and what exactly is the error?

Because knowing you spend a lot of time researching and learning things by surfing the web, was the error along the lines similar to:

While trying to load a webpage in a browser? That would imply a problem with either DNS or the website... A networking issue would be suspected.

Or was it something you saw on the splash screen while you were booting? That would be the computer hostname.

Here's the screenshot where the error happens; in the terminal. As far as I can tell, this error is not appearing anywhere else. Only in the terminal. Is there a way to fix this?

[https://drive.google.com/file/d/1kPX0mxY6thD9GlyatwooIP_iEQvujTiN/view?usp=sharing](https://drive.google.com/file/d/1kPX0mxY6thD9GlyatwooIP_iEQvujTiN/view?usp=sharing)

---

### Post by Advait on 2023-11-14
> **1fallen said:**
> Please check and show us:
```
 hostname
lvm-ThinkPad-X1-Carbon-7th
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> cat /etc/hostname 
lvm-ThinkPad-X1-Carbon-7th

```
The same hostname should be listed in the /etc/hosts file as well.

I copied and pasted that block of code into my terminal and it produced errors. Any way to run your block of code without errors? (I'm a newb, but that looks like a rather strange block of code. How can those lines and arrows be valid commands? If they're not commands, what are they for?)

```
advait@advait-Bravo-15-A4DDR:~$  hostname
lvm-ThinkPad-X1-Carbon-7th
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> cat /etc/hostname 
lvm-ThinkPad-X1-Carbon-7th
advait-Bravo-15-A4DDR
lvm-ThinkPad-X1-Carbon-7th: command not found
bash: syntax error near unexpected token `newline'
&#9474;~: command not found
&#9492;&#9472;: command not found
lvm-ThinkPad-X1-Carbon-7th: command not found
advait@advait-Bravo-15-A4DDR:~$ 

```

---

### Post by MAFoElffen on 2023-11-14
You copied "too much". LOL

The commands were 
```

hostname
cat /etc/hostname

```
1fallen's output for his hostname, when he did that on his computer was
```

lvm-ThinkPad-X1-Carbon-7th

```
Your output of the command was 
```

advait-Bravo-15-A4DDR

```
Which is the same displayed in your command prompt...

I followed your link to that screenshot, but it had me request permission from you to view it... Which it said was requested, and that I would receive an email confirming your approval when you do that... Waiting.

---

### Post by Advait on 2023-11-14
> **1fallen said:**
> Please check and show us:
```
 hostname
lvm-ThinkPad-X1-Carbon-7th
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> cat /etc/hostname 
lvm-ThinkPad-X1-Carbon-7th

```
The same hostname should be listed in the /etc/hosts file as well.

I made a guess and ran the commands separately. That wasn't specified but it seemed to work. Is this helpful?

```
advait@advait-Bravo-15-A4DDR:~$  hostname
advait-Bravo-15-A4DDR
advait@advait-Bravo-15-A4DDR:~$ cat /etc/hostname
advait-Bravo-15-A4DDR
advait@advait-Bravo-15-A4DDR:~$ 

```

---

### Post by Advait on 2023-11-14
> **MAFoElffen said:**
> I followed your link to that screenshot, but it had me request permission from you to view it... Which it said was requested, and that I would receive an email confirming your approval when you do that... Waiting.

Whoops, I changed the link to public access. Here it is. Working now?

[https://drive.google.com/file/d/1kPX0mxY6thD9GlyatwooIP_iEQvujTiN/view?usp=sharing](https://drive.google.com/file/d/1kPX0mxY6thD9GlyatwooIP_iEQvujTiN/view?usp=sharing)

---

### Post by Advait on 2023-11-14
> **MAFoElffen said:**
> You copied "too much". LOL

The commands were 
```

hostname
cat /etc/hostname

```
1fallen's output for his hostname, when he did that on his computer was
```

lvm-ThinkPad-X1-Carbon-7th

```
Your output of the command was 
```

advait-Bravo-15-A4DDR

```
Which is the same displayed in your command prompt...

I followed your link to that screenshot, but it had me request permission from you to view it... Which it said was requested, and that I would receive an email confirming your approval when you do that... Waiting.

Thanks. I saw this after I submitted my post below yours. Now it's more clear. It's helpful to say something like "Here's the commands. Run them one at a time and send us the results." I got confused by the lines and arrows, they didn't make any sense to me.

---

### Post by MAFoElffen on 2023-11-15
I saw it... That error comes up when the name in the /etc/hostname file does not match the name in the /etc/hosts file
```

grep . /etc/host* | grep -v 'allow\|deny'

```
Edit the name in the /etc/hosts file to match what it should be... We have already verified that the one on the /etc/hostname file is correct.
```

sudo nano /etc/hostname

```
It should be on the same line in that file, to the right of where it says "127.0.1.1"...

---

### Post by Advait on 2023-11-15
> **MAFoElffen said:**
> I saw it... That error comes up when the name in the /etc/hostname file does not match the name in the /etc/hosts file
```

grep . /etc/host* | grep -v 'allow\|deny'

```
Edit the name in the /etc/hosts file to match what it should be... We have already verified that the one on the /etc/hostname file is correct.
```

sudo nano /etc/hostname

```
It should be on the same line in that file, to the right of where it says "127.0.1.1"...

I edited the etc/hosts file and changed it from 127.0.1.1 to advait-Bravo-15-A4DDR (it was the only line in the file). Then I did a reboot. I checked and the etc/hosts file now only has advait-Bravo-15-A4DDR

But the problem still there:

```
advait@advait-Bravo-15-A4DDR:~$ sudo apt list &#8211;-installed
sudo: unable to resolve host advait-Bravo-15-A4DDR: Name or service not known
[sudo] password for advait: 
Listing... Error!
E: input:0-13: error: Expected pattern
   &#8211;-installed
   ^^^^^^^^^^^^^
advait@advait-Bravo-15-A4DDR:~$ 

```

Any way to fix this?

Here's a screenshot of the current etc/hosts file. It now matches the etc/hostname file.

[https://drive.google.com/file/d/1I0p5BAHe5KGzveghtOu4KD1PeFoLXC4M/view?usp=sharing](https://drive.google.com/file/d/1I0p5BAHe5KGzveghtOu4KD1PeFoLXC4M/view?usp=sharing)

---

### Post by tea for one on 2023-11-15
Have a close look at the second hyphen
```
sudo apt list –-installed [COLOR="#0000FF"]your version[/COLOR]
apt list --installed [COLOR="#0000FF"]try this[/COLOR]
```

---

### Post by Advait on 2023-11-15
> **tea for one said:**
> Have a close look at the second hyphen
```
sudo apt list –-installed [COLOR="#0000FF"]your version[/COLOR]
apt list --installed [COLOR="#0000FF"]try this[/COLOR]
```

I fixed that typo but the same error still seems to be there...? See below.

```
advait@advait-Bravo-15-A4DDR:~$ sudo apt list --installed
sudo: unable to resolve host advait-Bravo-15-A4DDR: Name or service not known
Listing... Done
```

---

### Post by Rubi1200 on 2023-11-15
In post #10 MAFoElffen gave you instructions:
> 
Edit the name in the **/etc/hosts** file to match what it should be... We have already verified that the one on the /etc/hostname file is correct.
Code:
sudo nano /etc/hostname
[COLOR=#ff0000]It should be on the same line in that file, to the right of where it says "127.0.1.1"[/COLOR]...


You need to edit the hosts file again. Since I assume you now have the correct hostname there just add 127.0.1.1 **before** your hostname and then save.

In other words,
```
sudo nano /etc/hosts

```

Make the change, save.

Everything good now?

---

### Post by Advait on 2023-11-15
> **Rubi1200 said:**
> In post #10 MAFoElffen gave you instructions:

You need to edit the hosts file again. Since I assume you now have the correct hostname there just add 127.0.1.1 **before** your hostname and then save.

In other words,
```
sudo nano /etc/hosts

```

Make the change, save. Everything good now?

Should the hostname file be *127.0.0.1 advait-Bravo-15-A4DDR* Or *127.0.0.1 localhost advait-Bravo-15-A4DDR* ? Another support person I'm working with suggested adding *localhost*.

Also, should the content of the **hosts** file exactly match the **hostname** file? If no, then what should be the contents of my **hosts** file?

---

### Post by Rubi1200 on 2023-11-15
I believe it should be > 127.0.0.1 localhost advait-Bravo-15-A4DDR

After saving you should restart the computer.

Keeping fingers crossed it will work now.

---

### Post by Advait on 2023-11-15
> **Rubi1200 said:**
> I believe it should be 

After saving you should restart the computer.

Keeping fingers crossed it will work now.

I made the change to **hosts** and rebooted. Yes, looks like this worked. No longer seeing the *unable to resolve host* error.

My **hostname** file is just *advait-Bravo-15-A4DDR*. Is that OK?

---

### Post by Rubi1200 on 2023-11-15
I'm really glad to hear it works now.

Please wait for MAFoElffen to confirm before marking as Solved.

---

### Post by Advait on 2023-11-15
> **Rubi1200 said:**
> I'm really glad to hear it works now.

Me, too. Thanks for your help!

> **Rubi1200 said:**
> Please wait for MAFoElffen to confirm before marking as Solved.

Sure, will do. So looks like MAFoElffen is the Chancellor Gowron of this forum. ;) :)

---

### Post by #&amp;thj^% on 2023-11-15
Looks to me like your good to go now. ;)
call us on your next miss-hap. :)
You should be picking up some real knowledge lately.

---

### Post by Advait on 2023-11-16
> **1fallen said:**
> Looks to me like your good to go now. ;)

Wait a minute. You're not MaFoElfin. Only he has the Magical Scepter of Solved Confirmation.

(smile, :) just teasing)


> **1fallen said:**
> call us on your next miss-hap. :)

I like your confidence that I'll be having future mishaps. :confused:  :D


> **1fallen said:**
> You should be picking up some real knowledge lately.

I'm definitely learning. I keep finding new ways to bork my system.  :D

---

### Post by MAFoElffen on 2023-11-16
Just looked at this... Stop. Take a breath Breathe...

Seems like your hosts file is missing a lot of things that should be there. So let's edit that and fix it.
```

sudo nano /etc/hosts

```
Edit it to this:
```

127.0.0.1    localhost
127.0.1.1    advait-Bravo-15-A4DDR
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```
Save and exit

Now for your error... Do the command correctly... Meaning the syntax for "apt list" is
```

apt list <package_match, required parameter> <options, optional parameter>

```
You were missing anything that it could match to... and since not there, read "--installed", and tried to process that as a package name, so failed.

Try this now...
```

apt list linux-*-generic --installed

```
Tell me what that comes up with... Then tell me what installed package you were looking for(?)

---

### Post by Advait on 2023-11-16
> **MAFoElffen said:**
> Seems like your hosts file is missing a lot of things that should be there. So let's edit that and fix it.
```

sudo nano /etc/hosts

```
Edit it to this:
```

127.0.0.1    localhost
127.0.1.1    advait-Bravo-15-A4DDR
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```
Save and exit

I entered in your suggested changes to the hosts file and rebooted. Seems to be working. No issues seen yet.

Shall I mark thread as Solved?

---

