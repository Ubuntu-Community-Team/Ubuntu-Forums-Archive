---
title: "symbolic Link to a http URL file? (*.php file)"
date: 2008-04-02
forum: General Help
---

### Post by luvit on 2008-04-02
i found a useful **php** file which is free to use, but i cannot redistribute in a live-cd i'm building.

i believe it needs to run locally on my server from a remote browser.
typically you download this file on your own server (but i cannot redistribute it on a live-cd).

is it possible to have a symbolic link on my live-cd of that file's http location so it executes as if it were located on my live-cd?

make sense? ;)
thanks!

---

### Post by ibuclaw on 2008-04-02
You can create a launcher, or an executable text file.

ie:
Right click, say on the desktop click "Create Launcher".
Give it any name or description you like.
Then in the command box type in:
```
 firefox http://www.google.com/linux 
```
for example.


On the other hand, an executable text file would look like this.
```

#!/bin/bash
firefox http://www.google.com/linux

```
Though I recommend going with a Launcher. They're so much easier. :)

Regards
Iain


By the way, what is the php file, and where exactly does it say that you are restricted to use it publicly?

---

### Post by luvit on 2008-04-02
i don't believe that's the answer i need...

my GUIless Ubuntu Server needs *install_file.php* at /var/www/installer/

i will access my server from a remote browser and execute the symbolic link of *[http://www.company.com/downloads/installer_file.php](http://www.company.com/downloads/installer_file.php)* as if it actually resided on my server at /var/www/installer/


heh... tough to picture, i'm sure. :)

i may be out of luck and have to resort to writting instruction book on file posting and executing, CHMODing, etc...

---

### Post by ibuclaw on 2008-04-02
hmm...  oops.
Didn't notice the "server" part of the question.

Yes it is tough to picture, as I can't imagine life without Firefox :)
hmm... 

I think there should most definitely be a way to do this.

Depends on how much security you need for the server.

For example, if your server isn't behind a router or hardware firewall. I think its possible to link it to the IP address of your server.
ie:
```
 123.45.678.90/var/www/installer/file.php 
```

Though some knowledge of scripting (probably javascript)  I would advise be required so your IP address appears hidden from view to the average onlooker.

Else I could be wrong, and you should really be looking at making an executable text file to run a batch script of downloading and using the file.
The command "**wget**" in the Linux terminal should be your best friend. It downloads absolutely anything from anywhere. (As long as you get the location right).

Regards
Iain

[EDIT]
[QUOTE=luvit] i may be out of luck and have to resort to writting instruction book on file posting and executing, CHMODing, etc... [/QUOTE]
If you can write an instruction book on what to do, you can most definately (99.99% of the time) write a batch script to do the job for you!
Do you know much about any shell scripts for UNIX?
I enjoy a small challenge, if you instruct me what it is that needs doing, I could come up with a small layout that you can alter to your needs, perhaps?

---

### Post by luvit on 2008-04-02
no... lulz
i'm not clear. i'll still give thanks, though :)

i think i have a work-around i'll test out soon.

---

