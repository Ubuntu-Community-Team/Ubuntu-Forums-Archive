---
title: "Problems with sources.list for installing 3rd party tools"
date: 2013-09-04
forum: General Help
---

### Post by abhayaasp on 2013-09-04
Well, i am the user of the ubuntu 12.04. I tried to install the 3rd party tools with the sudo apt-get .... but nothing is installing and the error mentioning the 
"Malformed line 60 in sources list/etc/apt/sources.list and sources of the line couldn't be read while trying to install from terminal. I tried to do the same stuff using the  update manager and the same error reporting and i have searched stuff and i found the similar post like me and same error and tried to fixed the error as mentioned in the answered section but none of the stuff helped and i am pasting contents of the "source.list" above.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
**deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner((line 60))**
deb [http://archive.canonical.com/](http://archive.canonical.com/) [distro] partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) [distro] partner
An unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:
E: Malformed line 60 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
plz help me.:icon_frown:

---

### Post by bluefrog on 2013-09-04
open "software sources". uncheck / check. should solve the problem.
otherwise get rid of the line or comment it.

---

### Post by abhayaasp on 2013-09-04
I haven't already installed software soureces so i opened the ubuntu software centre. it shows the crash report that ubuntu software center has closed unexpectedly. so, i can't resolve in that way. There's something on the line 60 which i can't figure it out.

---

### Post by steeldriver on 2013-09-04
Can you copy and paste the output of the following EXACTLY as it appears in the terminal please

```
cat -n /etc/apt/sources.list | sed '55,$!d'
```

Use CODE tags around the text to make it easier to read [HTML]```

```[/HTML]

---

### Post by abhayaasp on 2013-09-05
well, i typed of the following command in the terminal and i got the following result.
<code>
55	
    56	## This software is not part of Ubuntu, but is offered by third-party
    57	## developers who want to ship their latest software.
    58	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    59	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    60	deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
    61	deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
    62	deb [http://archive.canonical.com/](http://archive.canonical.com/) [distro] partner
    63	deb-src [http://archive.canonical.com/](http://archive.canonical.com/) [distro] partner
    64	
</code>

---

### Post by claracc on 2013-09-05
The url provided in line 60 : [http://archive.canonical.com/precise](http://archive.canonical.com/precise) drives to a "not found" error:

Not Found

The requested URL /precise was not found on this server.
Apache/2.2.22 (Ubuntu) Server at archive.canonical.com Port 80

So I would disable the 60 and 61 lines by typing  a # character in the beginning of each lines, then savand exit sources.list file and try to update again.

---

### Post by bluefrog on 2013-09-05
either that indeed or correct the lines to show "ubuntu"

60 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
61 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

and get rid of the others below (or comment them)

---

### Post by abhayaasp on 2013-09-05
Thanx . Problem resolved. :popcorn:

---

### Post by claracc on 2013-09-06
Please, mark the thread as solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Thanks

---

