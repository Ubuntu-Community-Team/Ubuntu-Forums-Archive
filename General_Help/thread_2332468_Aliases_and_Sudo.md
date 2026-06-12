---
title: "Aliases and Sudo"
date: 2016-08-01
forum: General Help
---

### Post by sirbearington on 2016-08-01
Hello,

I have set up aliases but if I want to user them I have to run sudo su or -i first.
What is the best workflow for getting around that? Should I try to make sure my shell always has root privileges or is there another way so I don't have to constantly input my password.

---

### Post by deadflowr on 2016-08-01
Where is the alias file you made/used located?
Or
Tell us more about how you went about creating your aliases.

---

### Post by sirbearington on 2016-08-02
I made a file /root/.bash_aliases aka /home/$USER/.bash_aliases
What the entire file looks like:

# Open New Private Firefox Window
alias fire='firefox --private-window'

# Open Alias File ~/.bash_aliases
alias openAli='gedit ~/.bash_aliases'

# Open Android Stuio
alias android='studio.sh'

---

### Post by deadflowr on 2016-08-02
> I made a file /root/.bash_aliases aka /home/$USER/.bash_aliases
?
Do you you mean you created it in /root and copied it to your user's /home folder?
Double check that your user has ownership.
/root and /home are totally different things.
And since you would need to access the /root folder with sudo, or as root, anything you move or copy from it would retain the root ownership.
So that might be where the problem lies.
But that's a guess.

---

### Post by sirbearington on 2016-08-07
I see what you mean now. My experience with Linux is not very technical.
I wasn't aware that /root and /home/$USER where different directories or accounts. I thought running sudo only gave my account root privileges and my confusion came from /home/$USER and /root having same files (.bashrc, .bash_aliases, etc) so I was editing the file on root and not in my user directory.

---

