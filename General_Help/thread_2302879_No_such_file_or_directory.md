---
title: "No such file or directory"
date: 2015-11-14
forum: General Help
---

### Post by kalantos on 2015-11-14
Yesterday I tried to install metasploit in order to play a little with armitage i follow a guide ([http://hackingforum.in/showthread.php?tid=5&pid=5#pid5](http://hackingforum.in/showthread.php?tid=5&pid=5#pid5)) and the part of ruby installing gave me an error, so i couldnt install metasploit (no problem with that, i make a virtual machine in Vbox with kali). But now when i open a new terminal or i enter a command i get this message one time and another "bash: /home/kalantos/.rvm/scripts/rvm: No such file or directory" want to know how can i fix that :D



Steps i follow
```
sudo apt-get install build-essential libreadline-dev libssl-dev  libpq5 libpq-dev libreadline5 libsqlite3-dev libpcap-dev openjdk-7-jre  git-core autoconf postgresql pgadmin3 curl zlib1g-dev libxml2-dev  libxslt1-dev vncviewer libyaml-dev curl zlib1g-dev
```

```
gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
=====Install RVM stable with ruby:
\curl -sSL https://get.rvm.io | bash -s stable --ruby
source ~/.rvm/scripts/rvm
echo "source ~/.rvm/scripts/rvm" >> ~/.bashrc
source ~/.bashrc
rvm install 2.1.6
rvm use 2.1.6 --default
ruby -v

 
```
a pic from my terminal 
[http://subefotos.com/ver/?dee76dafca08171864e8965dc1612cdfo.png](http://subefotos.com/ver/?dee76dafca08171864e8965dc1612cdfo.png)

---

### Post by matt_symes on 2015-11-14
Hi

```
echo "source ~/.rvm/scripts/rvm" >> ~/.bashrc
```

The above command that you entered into the terminal (in post #1), added the command

```
source ~/.rvm/scripts/rvm
```

to the file 

```
~/.bashrc
``` 

in your home directory. 

```
~/
``` is short hand for you home directory; in your case ```
/home/kalantos/
``` and get's expanded by the shell from *~/* into */home/kalantos/* when your bashrc is *source*d.

As the file/directory */home/kalantos/.rvm/scripts/rvm* does not exist (because of the failed install of ruby), bash gives you a warning when you start a new bash shell.

```
bash: /home/kalantos/.rvm/scripts/rvm: No such file or directory
```

Assuming this was the last edit you made to your ~/.bashrc file then you want to delete the last line in your ~/.bashrc file, as the '>>' redirection operator will append to the end of the file.

I.E *source ~/.rvm/scripts/rvm* gets appended to the file *~/.bashrc*.

You can remove that line using any text editor, or if you are confident it's the last line, with the command from the terminal.

```
sed -i '$d' ~/.bashrc
```

You can check the last line of your bashrc file using this command.

```
tail -n1 ~/.bashrc
```

Kind regards

---

### Post by kalantos on 2015-11-14
Thanks a lot! love the explanation, i follow the steps and fix it! and also learn a bit :D you rock!

---

### Post by matt_symes on 2015-11-14
Hi

No problem :)

I'll mark this thread as [SOLVED] for you.

Kind regards

---

