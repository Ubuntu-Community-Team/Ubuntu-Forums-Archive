---
title: "SYnaptic Package Manager not working"
date: 2008-07-04
forum: General Help
---

### Post by Twinemanzi on 2008-07-04
I am new to Ubuntu "Gutsy". When i try to activate my Synaptic Package Manager this is the error message i get. Right now i cannot even use the Update Manager either. Does anyone have a solution ? 

E: Type '<\DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by Elfy on 2008-07-04
Open aterminal and remove the file with this command, then run each of the following 2 commands seperately to get the medibuntu repo

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by Twinemanzi on 2008-07-04
As a follow up to my last post, the reason i was even looking at the Synaptic Package Manager was that when i tried to use add/remove in Ubuntu "gutsy" i got the message below. 


Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'

On trying to use Synaptic to check for broken packages,  i am getting the message below;


An error occured:

E: Type '<\DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Does anyone have any ideas or can anyone help me on this?

---

### Post by Elfy on 2008-07-04
emm... don't double post please - you'll find the answer in your other thread :)

You might not know but add/remove and synaptic are very similar - add/remove is just some of the stuff in synaptic, both of which are gui's for apt-get - if one doesn't work none will.

---

### Post by p_quarles on 2008-07-04
Threads merged. Please add information by editing or responding to the old post, not by starting a new thread.

---

### Post by Twinemanzi on 2008-07-04
Sorry about the double post. Your advice worked like a dream. Thank you.

---

