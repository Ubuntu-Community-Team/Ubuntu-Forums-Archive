---
title: "Installing VMware Player in 14.04"
date: 2014-10-19
forum: General Help
---

### Post by at2smithjason on 2014-10-19
I have an iPhone that I would like to use in the way that its intended with iTunes.  I was doing some research and it seemed like to me that VMware Player would be the best bet.  So I was looking at how to geek and getting instructions on how to install it so that I can use Windows parttime when I needed to update my iPhone.  What i entered the first command into the terminal this is what i got:

> smithfamily@smithfamily-Aspire-7741:~$ chmod +x ./VMware-Player-6.0.3-1895310.x86_64.bundle
chmod: cannot access ‘./VMware-Player-6.0.3-1895310.x86_64.bundle’: No such file or directory
smithfamily@smithfamily-Aspire-7741:~$ 

Is there something that I can do differently or is there a better option for me to get so that I can use the iPhone.  I also tried using the EZMP3 app that I saw that someone suggested in the Apple H/W subforum, but I didnt like that.

---

### Post by TheFu on 2014-10-19
Well, do the file, VMware-Player-6.0.3-1895310.x86_64.bundle, exist in the current directory?  Did you download it? Is it spelled exactly that way - case-sensitive?  Did you use tab-completion?

I ask just because it is unclear.  Did I misunderstand the issue?

---

### Post by at2smithjason on 2014-10-19
I do have the file downloaded, and its in my download folder and its not being seen, and I also placed t on my desktop with the same result.  Let me know if there is any other info that I can gather.

---

### Post by TheFu on 2014-10-20
> **at2smithjason said:**
> I do have the file downloaded, and its in my download folder and its not being seen, and I also placed t on my desktop with the same result.  Let me know if there is any other info that I can gather.

The command you attempted before requires that the bash session you are inside much have a CWD - current working directory - of the same place as the file. There was nothing wrong with the command. I suspect the file was not in the same CWD as was your terminal, but only you know how confident you are about that and how confident you are about running commands in a terminal.  Using chmod really isn't required for this basic CLI stuff. We can skip that.

The instructions here: [http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2053973](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2053973) are NOT for Ubuntu systems (though only slight changes are needed).

Run this:
**sudo bash ~/path/to/VMware-Player-6.0.3-1895310.x86_64.bundle**
but use tab-completion to ensure the exact spelling of the file/directories is 100% correct.  Something like **sudo bash ~/Desktop/VMware-Player-6.0.3-1895310.x86_64.bundle** should be close to the location you need (based on what you've said above).

To get better at CLI stuff, takes time. There is a great, free, PDF book here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) Skim it. Learning more CLI now will save you hours, days, weeks of frustration over things like this (which should be 1-2 seconds of effort).

Of course, if you are a wizard at CLI stuff already, then I've completely misunderstood the base issue and we need to step back to determine what happened.

---

