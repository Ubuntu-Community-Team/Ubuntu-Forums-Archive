---
title: "[SOLVED] reusing the  /var/cache/apt"
date: 2008-03-25
forum: General Help
---

### Post by sujoy on 2008-03-25
the situation is that i have a PC and a laptop. i keep my PC updated and do most of the downloads(from apt or synaptic) there, it has everything installed that i need. 

so all the packages are in /var/cache/apt folder of my PC. i dont want to download the same things for my laptop and yet do not want to install all the packages that are installed in my PC.

so i want the /var/cache/apt of my PC to act as a repository for my laptop, so that i can just select packages from synaptic and install them as needed (with all dependencies resolved by synaptic itself). how can i achieve this? 

i do not want to burn endless aptoncd discs, hence the repository idea..

---

### Post by Irihapeti on 2008-03-25
I think this may be what you are looking for:

[https://help.ubuntu.com/community/PersonalRepositories](https://help.ubuntu.com/community/PersonalRepositories)

I use this method to avoid having to download stuff again if I need to reinstall (I'm on dialup).

---

### Post by zvacet on 2008-03-25
Maybe you can find something else,but [this](https://help.ubuntu.com/community/Apt-Cacher-Server) is only thing I can think of right now.


> i do not want to burn endless aptoncd discs

If you have more then can fit to Cd use DVD.

---

### Post by sujoy on 2008-03-25
thanks for the responses, i will try them out and report :)

> If you have more then can fit to Cd use DVD.
yes but i meant that after i update again, i will need another disc..

anyways, the links looks promising, so i am off trying them out.


**EDIT:**

i followed the link to make a local repository on my PC
and then instead of adding it to the sources.list of my PC, i set up an ftp server and added the repo to my laptop as

> deb ftp: //username: password@desktophostname/../../var/cache/apt/archives  ./


thanks again. :)

---

