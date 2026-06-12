---
title: "Sharing Ubuntu folder  on Windows environment"
date: 2014-10-11
forum: General Help
---

### Post by ramsforums on 2014-10-11
Greetings :)

I have my office laptop which is authenticated to my office domain which runs on Windows 7 Enterprise.
Example my Domain is America.abcco.com
My computer name is DC2211

My office do not have reliable backup. So I have used my old Desktop PC and install LUbuntu in my Home computer. So I bring my office laptop to home and manually copy certain folders.

Now I want to share my LUbuntu folder with my office Laptop at home. Home PC is not connected to office domain but at home all computers on the same network. I can't change the office domain because joining back to domain requires approval.

How do I share my Hope PC folder with my Office Laptop when I am at home

Thanks

---

### Post by ecophobia on 2014-10-11
Sounds like a violation of your org's Information Security policy to me. :lolflag:
If you can connect to you home network, it should be easy - just network share the folder and browse the network with Win explorer. 
You should have network profiles on your work computers that you can select. One is related to your work (domain) and one should be configurable for use outside the org network.

Regarding joining back the domain, if you have a valid user name and password combo, 
you don't need re-joining the domain, you just log into the domain when you come back to work.

It is not very clear what the config is that you described. What is preventing you from using a portable USB drive for backups instead?

---

