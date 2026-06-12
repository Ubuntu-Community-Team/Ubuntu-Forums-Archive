---
title: "Can not run script"
date: 2008-03-16
forum: General Help
---

### Post by infinitezero on 2008-03-16
I have created a script to clone my hard drive every night, by opening a text file and adding the following: dd if=/dev/sda of=/dev/sdb bs=1M then saving the file as clone.sh. I have made it executable but it will still not run, what am I doing wrong?



Thanks,
iz

---

### Post by banewman on 2008-03-16
Can you post the whole script?
The first line in the script should be 
#!/bin/sh
:)

---

### Post by infinitezero on 2008-03-16
I only have dd if=/dev/sda of=/dev/sdb bs=1M in it, that is probably what I am doing wrong. So, I need to add #!/bin/sh to the beginning of the script. I will give it a try.

iz

---

### Post by banewman on 2008-03-16
Let us know how it goes pls.
:)

---

### Post by infinitezero on 2008-03-16
Banewman,
One more quick question, I thought that by adding # in front of a line commented it out? Is it different in scripts?

Thanks,
iz

---

### Post by drubin on 2008-03-16
It is called a Shebang line. basicly it tells the system what application to run the script with.

Take a look
[Shebang]("http://en.wikipedia.org/wiki/Shebang_(Unix)")

---

### Post by infinitezero on 2008-03-17
Banewman,

I added, "#!/bin/sh" to the script and that did the trick, thanks for the help.



iz

---

### Post by p_quarles on 2008-03-17
Thread moved to General Help, since Bash scripting has little to with any particular DE or window manager.

---

