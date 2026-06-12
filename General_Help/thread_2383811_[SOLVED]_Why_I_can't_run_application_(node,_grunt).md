---
title: "[SOLVED] Why I can't run application (node, grunt) on www-data user?"
date: 2018-01-29
forum: General Help
---

### Post by satriaf on 2018-01-29
On my Ubuntu 16.04.3, I can't run some applications like node, grunt, etc on www-data user. 
```
teddy@teddy:~/var/www/html/magento2$ sudo su -s /bin/bash www-data
www-data@teddy:/var/www/html/magento2$ grunt
No command 'grunt' found, did you mean:
 Command 'grun' from package 'grun' (universe)
grunt: command not found
```

I already installed the applications and they run well outside www-data user
```
teddy@teddy:~/var/www/html/magento2$ grunt
Running "default" task

I'm default task and at the moment I'm empty, sorry :/

Done, without errors.


Execution Time (2018-01-30 11:49:58 UTC+7)
loading tasks  138ms  &#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607;&#9607; 99%
default          2ms  &#9607; 1%
Total 140ms
```

How to make those applications run on www-data user?

EDIT: I installed nodejs via NVM (Node.js version manager).
```
teddy@teddy:~$ which node
/home/teddy/.nvm/versions/node/v8.9.4/bin/node
teddy@teddy:~$ which grunt
/home/teddy/.nvm/versions/node/v8.9.4/bin/grunt
```

---

### Post by btindie on 2018-01-30
It's because you've installed *nvm* locally to your *teddy* account.

You need to either install it globally, or local to your *www-data* account.

[https://github.com/creationix/nvm](https://github.com/creationix/nvm)
> [COLOR=#24292E][FONT=-apple-system]You can customize the install source, directory, profile, and version using the [/FONT][/COLOR]NVM_SOURCE[COLOR=#24292E][FONT=-apple-system], [/FONT][/COLOR]NVM_DIR[COLOR=#24292E][FONT=-apple-system], [/FONT][/COLOR]PROFILE[COLOR=#24292E][FONT=-apple-system], and [/FONT][/COLOR]NODE_VERSION[COLOR=#24292E][FONT=-apple-system] variables. Eg: [/FONT][/COLOR]curl ... | NVM_DIR=/usr/local/nvm bash[COLOR=#24292E][FONT=-apple-system] for a global install.[/FONT][/COLOR]

---

### Post by satriaf on 2018-01-30
I removed my old nvm directory in ~/.nvm then reinstalled it again. I have to use root user to install it because I dont get permission to install nvm in /usr/local directory
```
 teddy@teddy:~$ sudo su
root@teddy:/home/teddy# curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | NVM_DIR=/usr/local/nvm bash
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 12540  100 12540    0     0  38705      0 --:--:-- --:--:-- --:--:-- 38823
=> Downloading nvm from git to '/usr/local/nvm'
=> Cloning into '/usr/local/nvm'...
remote: Counting objects: 264, done.
remote: Compressing objects: 100% (229/229), done.
remote: Total 264 (delta 31), reused 107 (delta 25), pack-reused 0
Receiving objects: 100% (264/264), 116.46 KiB | 0 bytes/s, done.
Resolving deltas: 100% (31/31), done.
Checking connectivity... done.
Note: checking out '7ad6d98cedde01809e32d56ab8ced064f6f28175'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

=> Compressing and cleaning up git repository

=> Appending nvm source string to /root/.bashrc
=> Appending bash_completion source string to /root/.bashrc
=> Close and reopen your terminal to start using nvm or run the following to use it now:

export NVM_DIR="/usr/local/nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

Then run 'source ~/.bashrc' command. But I got nothing when I run 'command -v nvm' with my 'teddy' user. To make it work, I have to add this manually in ~/.bashrc 
```
export  NVM_DIR="/usr/local/nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
``` 

But on 'www-data' user, this is still not working.

---

### Post by satriaf on 2018-01-30
I can't make nvm work for www-data user if I install it outside www-data (even on root user). It seemed I have to install nvm, node and grunt right on www-data user. 
First I have to create .nvm and .npm directory in /var/www directory then set those new directories to www-data user:
```
 
teddy@teddy:~$ cd /var/www/ 
teddy@teddy:/var/www$ sudo mkdir .nvm 
teddy@teddy:/var/www$ sudo mkdir .npm 
teddy@teddy:/var/www$ sudo chown www-data -R .nvm/ .npm/
```

Then log as www-data user to install nvm
```
 
teddy@teddy:/var/www$ cd ~
teddy@teddy:~$ sudo su -s /bin/bash www-data
www-data@teddy:/home/teddy$ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 12540  100 12540    0     0  41152      0 --:--:-- --:--:-- --:--:-- 41250
=> Downloading nvm from git to '/var/www/.nvm'
=> Cloning into '/var/www/.nvm'...
remote: Counting objects: 264, done.
remote: Compressing objects: 100% (229/229), done.
remote: Total 264 (delta 31), reused 107 (delta 25), pack-reused 0
Receiving objects: 100% (264/264), 116.46 KiB | 0 bytes/s, done.
Resolving deltas: 100% (31/31), done.
Checking connectivity... done.
Note: checking out '7ad6d98cedde01809e32d56ab8ced064f6f28175'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

=> Compressing and cleaning up git repository

=> Profile not found. Tried ~/.bashrc, ~/.bash_profile, ~/.zshrc, and ~/.profile.
=> Create one of them and run this script again
   OR
=> Append the following lines to the correct file yourself:

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
=> Close and reopen your terminal to start using nvm or run the following to use it now:

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm

```

then modify /etc/bash.bashrc file to add these two lines at the bottom:
```

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm

```

then run: source /etc/bash.bashrc
back to the terminal (close and reopen it would be better) to check nvm version & install node & grunt (assumed nvm is working):
```

teddy@teddy:~$ sudo su -s /bin/bash www-data
[sudo] password for teddy: 
www-data@teddy:/home/teddy$ nvm --version
0.33.8
www-data@teddy:/home/teddy$ nvm install 8.9.4
Downloading and installing node v8.9.4...
Downloading https://nodejs.org/dist/v8.9.4/node-v8.9.4-linux-x64.tar.xz...
######################################################################## 100,0%
Computing checksum with sha256sum
Checksums matched!

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474;               npm update check failed                &#9474;
&#9474;         Try running with sudo or get access          &#9474;
&#9474;         to the local update config store via         &#9474;
&#9474; sudo chown -R $USER:$(id -gn $USER) /var/www/.config &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
Now using node v8.9.4 (npm v5.6.0)
Creating default alias: default -> 8.9.4 (-> v8.9.4)
www-data@teddy:/home/teddy$ node -v
v8.9.4
www-data@teddy:/home/teddy$ npm -v
5.6.0
 
www-data@teddy:/home/teddy$ npm install -g grunt
npm WARN deprecated coffee-script@1.10.0: CoffeeScript on NPM has moved to "coffeescript" (no hyphen)
/var/www/.nvm/versions/node/v8.9.4/bin/grunt -> /var/www/.nvm/versions/node/v8.9.4/lib/node_modules/grunt/bin/grunt
+ grunt@1.0.1
added 92 packages in 3.375s

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474;               npm update check failed                &#9474;
&#9474;         Try running with sudo or get access          &#9474;
&#9474;         to the local update config store via         &#9474;
&#9474; sudo chown -R $USER:$(id -gn $USER) /var/www/.config &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
www-data@teddy:/home/teddy$ grunt -V
grunt-cli v1.2.0

```

I don't know why I got ' npm update check failed' message but anyway it's working now

---

