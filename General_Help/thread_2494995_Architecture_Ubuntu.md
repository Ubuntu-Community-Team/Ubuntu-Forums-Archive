---
title: "Architecture Ubuntu"
date: 2024-02-03
forum: General Help
---

### Post by tuan-93 on 2024-02-03
I want to know about the architecture, characteristics, components of the security system, security tools of Ubuntu, can someone give me the documentation?

---

### Post by TheFu on 2024-02-03
If you google this "Linux Security Architecture", the top few links seem related.

All of this will get very deep in terms you may not know. There's no jumping into the middle for most Unix skills.  We have to each start as beginners then add slightly more difficult skills over the decades, allowing our minds time to digest all the new information, place it into compartments and make connections between different compartments. I can't speak for others, but as I learn more and more, I see connections that just a few years ago, I wasn't ready to make between the different subsystems. 

One of the most important connections is that there are only 2 types of things on any Unix system.  A file and a process.  A process is currently running and shows up in the process table.  Everything else is a file, by definition.  Files have certain properties, including security properties.  Understanding and leveraging these properties in non-obvious ways can be used for security.

Ubuntu isn't special.  It is like every other Debian-based Linux, which is much like every other Linux, which is very similar to every Unix-like OS.  It uses a layered approach for almost everything, so that each layer would have a different architecture, dependent on the layers above and below.
The main difference between RHEL-based distros and Debian-based distros from a security standpoint is that RHEL uses SELinux and Debian uses AppArmor.  You can read up on each of those.

Hundreds of books have been written on the subject.  Additionally, the code is available for almost everything in any Linux system (except proprietary drivers) so you can get into the lowest level of details.

Often times, things that are critical to security are not labeled as such.

So, I'd recommend that you start by reading a Unix Architecture book. [https://www.interviewbit.com/blog/unix-architecture/](https://www.interviewbit.com/blog/unix-architecture/) is an overview. For more Linux-specific details, move to the TLDP - [https://tldp.org/](https://tldp.org/) .

As for specific security tools, you have to remember that Linux distros are 20K projects, put together, ad hoc. There's not really a centralized "do everything" team like commercial OSes have.  It is a vastly different philosophy about how an OS is created and installed.  [https://en.wikipedia.org/wiki/The_Cathedral_and_the_Bazaar](https://en.wikipedia.org/wiki/The_Cathedral_and_the_Bazaar) is a popular analogy.

---

### Post by dragonfly41 on 2024-02-03
I often ask myself the question "why" is this required by OP. Particularly a first post. That is, more context is always helpful.
[COLOR=#000000]
>  .. from TheFu .. allowing our minds time to digest 
[/COLOR][COLOR=#000000]all the new information, place it into compartments and make connections between different compartments.[/COLOR]
[COLOR=#000000]I don't know why quote breaks into two quotes?

As I continue my own learning path I now consider how to compartment knuggets of learning.

I am drawn towards experimenting with a vector database rather than countless notes and commands.
[/COLOR] [COLOR=#000000]
Order out of chaos.[/COLOR]  So back to the OP question. Defining security vectors is relevant.

[COLOR=#000000]
[/COLOR] [COLOR=#000000]

[/COLOR]

---

### Post by ajgreeny on 2024-02-03
There is, as said above, no quick or simple way to answer the question you posed as security of any operating system is incredibly multi-faceted and complicated that even the best experts on this forum can not give you what you want.

There is a section of the forum specifically related to security but it will take a very long time to understand it all and I am certain the majority of us never will.  However have a look at the post at [https://ubuntuforums.org/showthread.php?t=510812](https://ubuntuforums.org/showthread.php?t=510812) which though 17 years old still has much to say that is of value.

Do not forget that Ubuntu is very different from whatever you used in the past (Windows?) and does not need the same protection for some of the things that you are probably used to using to secure your OS, particularly anti-virus

---

