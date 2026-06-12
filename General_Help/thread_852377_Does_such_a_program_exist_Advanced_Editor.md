---
title: "Does such a program exist? Advanced Editor"
date: 2008-07-07
forum: General Help
---

### Post by markayler on 2008-07-07
So..I have a couple .cfg files that I want to modify. 

Each .cfg file has a specific word or number (ip address). I want to change the ip address to a name. I can easily use the find and replace feature using my favorite editor (nano) but I'm wondering if there exists a more advanced editor that has a find and replace feature but spans multiple files (files that I specify). 
I only have cli access but I could create an ssh share so that I can open these files with Open Office. Maybe I could create a macro? 

Anyone ever wonder about this? Better yet, anyone figure out if such an editor exists?  

If I wasn't clear enough, here is an example. I need to change the ip addresses to names. 

10.1.1.2 will be edge-admin.dc.ntwk
This needs to be changed in both .cfg files.

example1.cfg 

host2 = 10.1.1.2
host3 = 10.1.1.3

example1.1.cfg

host2 = 10.1.1.2
host3 = 10.1.1.3

So there are two sample .cfg files. Simple. Instead of opening each .cfg file and changing the ipaddress to the name, I want to tell the editor to change 10.1.1.2 to edge-admin.dc.ntwk in both files.

---

### Post by sdennie on 2008-07-07
This sounds like a job for sed.  Test the output with:

```

sed -e 's/10.1.1.2/edge-admin.dc.ntwk/' file1 file2 file3 ...

```

To make it permanent, just add the -i option:

```

sed -ie 's/10.1.1.2/edge-admin.dc.ntwk/' file1 file2 file3 ...

```

---

### Post by MacAnthony on 2008-07-07
How about sed?

```

sed 's/10.1.1.2/host2' *.cfg

```

---

### Post by markayler on 2008-07-07
I think that's what I'm looking for!
I ran the commands but it's not working. I'll do some googling to figure it out. Thanks!

---

### Post by sdennie on 2008-07-07
I never remember how to use sed so always end up referring to this guide: [http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html).  Very thorough and easy to understand.

---

### Post by markayler on 2008-07-07
Proper syntax was:

sed -i 's/10.1.1.2/gw-rtr-e0-secret-gs.nsa.ntwk/g' test.cfg test1.cfg

Thanks for the help!

---

