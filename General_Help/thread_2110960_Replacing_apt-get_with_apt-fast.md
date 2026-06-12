---
title: "Replacing apt-get with apt-fast"
date: 2013-01-31
forum: General Help
---

### Post by Hishighness on 2013-01-31
I read an article called 20 Things I did After Installing Ubuntu 12.10 Quantal Quetzal and it recommended a program called apt-fast that replaces apt-get.

I'm just wondering is there any way I can make my system use apt-fast even if I type apt-get? Stupid question I know but save me manually changing it every time I copy and past a get link from the web.

Thanks for your time,
H2

---

### Post by tgalati4 on 2013-01-31
You could put an *alias* in your .bashrc file.

Something like:

# some more aliases
alias hs='history'
alias ll='ls -l'
alias la='ls -A'
alias l='ls -CF'
alias cp='cp -i'
alias rm='rm -i'
alias mv='mv -i'
alias psa='ps -aux | more'

alias apt-get='apt-fast'

Do you have a web link for instructions on how to set up apt-fast?

---

### Post by Hishighness on 2013-01-31
> **tgalati4 said:**
> Do you have a web link for instructions on how to set up apt-fast?Firstly, thank you for the help.

Secondly, as I said I first heard about it in the above mentioned article. I followed the instructions there.

[http://www.techdrivein.com/2012/10/20-things-to-do-after-installing-ubuntu1210-quantal-quetzal.html](http://www.techdrivein.com/2012/10/20-things-to-do-after-installing-ubuntu1210-quantal-quetzal.html)

> Apt-Fast Accelerates your Apt Download Speeds
This one is for those among you who likes to mess around with command line tools.
Apt-fast is a simple command line utility that can make installation and upgrading of softwares in Ubuntu/Debian much faster. Apt-fast make use of Axel application which accelerates HTTP/FTP downloads by using multiple sources for one file.
Simply do the following in Terminal to install Apt-fast.

[I]sudo add-apt-repository ppa:apt-fast/stable
sudo apt-get update
sudo apt-get install apt-fast[/I]

Afterwards, a prompt will open up asking you to choose between apt-get and aptitude. Again, another prompt pops up asking to to choose between Axel and Aria2c (download managers). Choose the ones you like and you're done (I prefer apt-get and axel). 
Now, simply replace apt-get in commands with apt-fast. Examples below:

[I]sudo apt-fast install chromium-browser
sudo apt-fast upgrade[/I]

Done. Enjoy your increased apt-get download speeds.

---

