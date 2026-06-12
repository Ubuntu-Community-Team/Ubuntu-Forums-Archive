---
title: "So many problems...never had these before when installing java"
date: 2013-08-22
forum: General Help
---

### Post by Deery50 on 2013-08-22
So on a complete fresh install of Ubuntuserver I just installed these programs:
OpenJDK-jre7
OpenJDK-jdk7

and...for some reason errors galore.
I restarted the computer many times but every time I run my server I get spammed with these errors: java.lang.NoClassDefFoundError: sun/net/www/protocol/http/HttpURLConnection
For a full log example: [http://pastebin.com/HF1HGyPP](http://pastebin.com/HF1HGyPP)
Any help at all is appreciated as searching everywhere on every forum I could find yielding no results.

[edit]
This is what I get by running a simple Minecraft server: [http://pastebin.com/TDWtDi2R](http://pastebin.com/TDWtDi2R)
I also just relialized I am getting these messages from the main console: [http://pastebin.com/3aW3uVKj](http://pastebin.com/3aW3uVKj)

---

### Post by Cheesemill on 2013-08-23
All the ATA errors your getting on the console point to a failing disk or a loose HD cable.

Try running a SMART test on your drive to check if it's OK.

---

### Post by Deery50 on 2013-08-23
> **Cheesemill said:**
> All the ATA errors your getting on the console point to a failing disk or a loose HD cable.

Try running a SMART test on your drive to check if it's OK.

I just bought this hard drive...I'm sorry what is a SMART test?

Figured it out, results from test: [http://pastebin.com/rtc6L8dL](http://pastebin.com/rtc6L8dL) (I'm not sure what any of this means but It is apparent that there is a problem)

[edit]
Re-installed Ubuntu, same log. Is my bran new hard disk DOA?

[edit]
But...For some reason I do not believe I am getting the java errors when I re-installed ubuntu-server.

---

### Post by Deery50 on 2013-08-23
I am no longer getting either of the errors...but should I still be worried?

---

