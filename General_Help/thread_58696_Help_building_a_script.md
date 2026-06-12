---
title: "Help building a script"
date: 2005-08-21
forum: General Help
---

### Post by xodeus on 2005-08-21
Please help building a script to remote reboot router.

here's the lines to the script

#Connecting to router
telnet 192.168.1.1

#Enter first password 1 caracter pr. second
abcdefgh

#Go to enable mode
enable

#Enter the enable mode password like the first 1 caracter pr. second
abcdefg

#Reload command
reload

#then the confirmation
y

#when done print on screen router reset finnished.
echo Router Reset Complete

#quit
quit

---------------------------------

can this be done.
Here's what it looks like in the console.

mariusz@networkadmin101c:~$ telnet 192.168.1.1
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.


User Access Verification

Password:
6x00p030>enable
Password:
6x00p030#reload
Proceed with reload? [confirm]yConnection closed by foreign host.
mariusz@networkadmin101c:~$

---

### Post by heimo on 2005-08-21
Is installing ssh-server impossible? (it's not generic PC hardware?)

EDIT: Oh, I believe so. You may want to check what you can do with netcat (nc).

---

### Post by AnythingBut on 2005-08-21
Yeah.  I think netcat is the way to go.  You can put the login and router command in a text file as it would be typed then use:

cat text | nc -t 192.168.1.1 25

You wont be able to get it to echo before its done though.

---

### Post by tomchuk on 2005-08-21
I've done similar things with python and telnetlib before, unfortunately I don't have access to my old code. Here's something simple to start from:

```

#!/usr/bin/env python

import sys
import telnetlib

HOST="192.168.1.1"
# it doesn't look like you need to login with a user, but for completeness:
USER="root"
PASS="abcdefgh"

# Connect to host
tn = telnetlib.Telnet(HOST)

# Read until first Password prompt, and enter pass, make sure that the 
# password prompt includes a space after it, or delete the space in the 
# followinf string. ie turn "Password: " into "Password:"

tn.read_until("Password: ")
tn.write(PASS + "\n")

# Write "enable"
tn.write("enable" + "\n")

# Read until pass and enter it. Again, correct for the space at the end of the
# prompt if you need to.
tn.read_until("Password: ")
tn.write(PASS + "\n")

# Write reload and 'y' to confirm
tn.write("reload" + "\n")
tn.read_until("[confirm]")
tn.write("y" + "\n")

# close up
tn.close()

```

Example [here](http://www.python.org/doc/2.3.5/lib/telnet-example.html) and Object reference [here](http://www.python.org/doc/2.3.5/lib/telnet-objects.html).

---

### Post by xodeus on 2005-08-23
[QUOTE=heimo]Is installing ssh-server impossible? (it's not generic PC hardware?)

EDIT: Oh, I believe so. You may want to check what you can do with netcat (nc).[/QUOTE]
 Sorry for my slow replies.
But the router is a cisco 827 so I don't think so.

---

### Post by xodeus on 2005-08-23
[QUOTE=AnythingBut]Yeah.  I think netcat is the way to go.  You can put the login and router command in a text file as it would be typed then use:

cat text | nc -t 192.168.1.1 25

You wont be able to get it to echo before its done though.[/QUOTE]
This really works.
Can it be done in one file script though. So I can place it on my desktop and just doubleclick when needed??
Thanks

---

### Post by xodeus on 2005-08-23
[QUOTE=tomchuk]
Example [here](http://www.python.org/doc/2.3.5/lib/telnet-example.html) and Object reference [here](http://www.python.org/doc/2.3.5/lib/telnet-objects.html).[/QUOTE]
 I Rewrote the script but something is not right. When trying to run my cursor turns to an cross on screen. After 30 seconds I got this.
```
Router Reboot: line 13: syntax error near unexpected token `('
Router Reboot: line 13: `tn = telnetlib.Telnet(HOST)'
```
Then I changed the line ```
# Connect to host
tn = telnetlib.Telnet(HOST)
``` to ```
# Connect to host
tn = telnetlib.telnet(HOST)
``` so my file looks like this:
```
#!/usr/bin/env python

import sys
import telnetlib

HOST="192.168.1.1"
# it doesn't look like you need to login with a user, but for completeness:
USER="root"
PASS1="abcdefgha"
PASS2="zhdjeksla"

# Connect to host
tn = telnetlib.telnet(HOST)

# Read until first Password prompt, and enter pass, make sure that the 
# password prompt includes a space after it, or delete the space in the 
# followinf string. ie turn "Password: " into "Password:"

tn.read_until("Password: ")
tn.write(PASS1 + "\n")

# Write "enable"
tn.write("enable" + "\n")

# Read until pass and enter it. Again, correct for the space at the end of the
# prompt if you need to.
tn.read_until("Password: ")
tn.write(PASS2 + "\n")

# Write reload and 'y' to confirm
tn.write("reload" + "\n")
tn.read_until("[confirm]")
tn.write("y" + "\n")

# close up
tn.close()
``` 
But I can't get it working.

---

### Post by xodeus on 2005-08-25
BUMP

---

