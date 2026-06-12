---
title: "Java on firefox"
date: 2005-07-26
forum: General Help
---

### Post by jarg on 2005-07-26
I followed the instructions on [The Unoffical guide](http://ubuntuguide.org/#jre) exactly and am getting a weird error:

> E: Some packages could not be authenticated

I get this after it asks if I want to "install these packages without verification" and I say "y"
What exactly does this mean?

---

### Post by jesse on 2005-07-26
This is just because java is not included automatically in Ubuntu because of its license and is being installed from a non-Ubuntu repository. As long as you know for sure the site you're getting the java from is safe, you don't have to worry and can ignore these silly error messages. 

Can you post the repository?

---

### Post by jarg on 2005-07-26
[QUOTE=jesse]Can you post the repository?[/QUOTE]

I just started with linux, I don't even know for sure what that is. the second step tells me to basicly paste that over the other file. So in short I have no clue. Does the guide leave something out? Do I have to place a url somewhere.

---

### Post by NeoChaosX on 2005-07-26
Oh, I know. You're downlading Java from the Ubuntu Backports repos (they're referenced in the last couple of lines in what you pasted). It's just that the Backports servers don't have any authentication for their packages to make sure they're not fakes. You can download and install them normally without any problems, though.

---

### Post by jarg on 2005-07-27
[QUOTE=NeoChaosX]You can download and install them normally without any problems, though.[/QUOTE]

What is normaly? Remember I have only had linux a few days.

---

### Post by jesse on 2005-07-27
It means that since the program comes from the backports you can just ignore the silly warnings about authentication and just let them install.  :)

---

### Post by jarg on 2005-07-27
[QUOTE=jesse]It means that since the program comes from the backports you can just ignore the silly warnings about authentication and just let them install.  :)[/QUOTE]

my terminal says > Install these packages without verification [y/N]?
I put > y(I assume this means yes)

yet it gives me the error > E: Some packages could not be authenticatedeven though I do not want to verify them.** I am trying to ignore the warnings but it won't let me.**


An entire quote of the terminal.
> jared@ubuntu:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  libgtk1.2
The following NEW packages will be installed:
  sun-j2re1.5
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.5MB of archives.
After unpacking 89.1MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  sun-j2re1.5
Install these packages without verification [y/N]? y
E: Some packages could not be authenticated
jared@ubuntu:~$


---

### Post by mcrofutt on 2005-07-27
I get the same error. I even went and installed the package from SUN.Java and still no Java in Moz.,Firefox, or Epiphany browsers. Is there an alternative java package that will integrate?
 I've been looking at Google and I see a few others that are OS. Anyone know if they'll integrate into Ubuntu and our browsers?

---

### Post by jesse on 2005-07-27
Try using synaptic instead of the terminal.

Start synaptic (type "sudo synaptic" at the terminal and enter your password when prompted). 

Then reload the package list in synaptic and do a search for "sun". You should find "sun-j2re1.5" or something similar among the packages with "sun" in their name. Install it and ignore the authentication warnings.

---

### Post by jarg on 2005-07-27
[QUOTE=jesse]Try using synaptic instead of the terminal.

Start synaptic (type "sudo synaptic" at the terminal and enter your password when prompted). 

Then reload the package list in synaptic and do a search for "sun". You should find "sun-j2re1.5" or something similar among the packages with "sun" in their name. Install it and ignore the authentication warnings.[/QUOTE]

Thank you.  :)  It worked.

I wonder why the regular thing didn't work?

---

