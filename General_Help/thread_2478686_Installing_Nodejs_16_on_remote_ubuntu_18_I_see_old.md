---
title: "Installing Nodejs 16 on remote ubuntu 18 I see old nodejs 14 version?"
date: 2022-09-02
forum: General Help
---

### Post by nilovsergey on 2022-09-02
Hello,
I want to upgrade nodejs on my remote ubuntu 18.


I run update commands, I do not see any errors, but checking node version at the end I see old 14 version... 


```
    root@nsn-do-lamp:~# uname -a
    Linux nsn-do-lamp 4.15.0-191-generic #202-Ubuntu SMP Thu Aug 4 01:49:29 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
    root@nsn-do-lamp:~# sudo apt update
    Hit:1 http://ppa.launchpad.net/certbot/certbot/ubuntu bionic InRelease
    Hit:2 https://download.docker.com/linux/ubuntu bionic InRelease                                                                                                                                                  
    Hit:3 http://ppa.launchpad.net/ondrej/php/ubuntu bionic InRelease                                                                                                                                                
    Hit:4 https://deb.nodesource.com/node_16.x bionic InRelease                                                                                                                                                      
    Hit:5 http://mirrors.digitalocean.com/ubuntu bionic InRelease                                                                                     
    Hit:6 http://mirrors.digitalocean.com/ubuntu bionic-updates InRelease                                                       
    Ign:7 http://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/6.0 InRelease                                                   
    Hit:8 http://mirrors.digitalocean.com/ubuntu bionic-backports InRelease                        
    Hit:9 http://security.ubuntu.com/ubuntu bionic-security InRelease        
    Hit:10 http://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/6.0 Release 
    Reading package lists... Done                      
    Building dependency tree       
    Reading state information... Done
    15 packages can be upgraded. Run 'apt list --upgradable' to see them.
    root@nsn-do-lamp:~# curl -sL https://deb.nodesource.com/setup_16.x | sudo bash - 
    
    ## Installing the NodeSource Node.js 16.x repo...
    
    
    ## Populating apt-get cache...
    
    + apt-get update
    Hit:1 http://ppa.launchpad.net/certbot/certbot/ubuntu bionic InRelease
    Hit:2 http://security.ubuntu.com/ubuntu bionic-security InRelease                                                                                                                                                
    Hit:3 https://download.docker.com/linux/ubuntu bionic InRelease                                                                                                                                                  
    Hit:4 https://deb.nodesource.com/node_16.x bionic InRelease                                                                                                                                                      
    Hit:5 http://ppa.launchpad.net/ondrej/php/ubuntu bionic InRelease                                                                               
    Hit:6 http://mirrors.digitalocean.com/ubuntu bionic InRelease                                  
    Hit:7 http://mirrors.digitalocean.com/ubuntu bionic-updates InRelease    
    Ign:8 http://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/6.0 InRelease
    Hit:9 http://mirrors.digitalocean.com/ubuntu bionic-backports InRelease  
    Hit:10 http://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/6.0 Release
    Reading package lists... Done                      
    
    ## Confirming "bionic" is supported...
    
    + curl -sLf -o /dev/null 'https://deb.nodesource.com/node_16.x/dists/bionic/Release'
    
    ## Adding the NodeSource signing key to your keyring...
    
    + curl -s https://deb.nodesource.com/gpgkey/nodesource.gpg.key | gpg --dearmor | tee /usr/share/keyrings/nodesource.gpg >/dev/null
    
    ## Creating apt sources list file for the NodeSource Node.js 16.x repo...
    
    + echo 'deb [signed-by=/usr/share/keyrings/nodesource.gpg] https://deb.nodesource.com/node_16.x bionic main' > /etc/apt/sources.list.d/nodesource.list
    + echo 'deb-src [signed-by=/usr/share/keyrings/nodesource.gpg] https://deb.nodesource.com/node_16.x bionic main' >> /etc/apt/sources.list.d/nodesource.list
    
    ## Running `apt-get update` for you...
    
    + apt-get update
    Hit:1 http://ppa.launchpad.net/certbot/certbot/ubuntu bionic InRelease
    Hit:2 http://security.ubuntu.com/ubuntu bionic-security InRelease                                                                                                                                                
    Ign:3 http://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/6.0 InRelease                                                                                                                                        
    Hit:4 https://deb.nodesource.com/node_16.x bionic InRelease                                                                                                                                        
    Hit:5 https://download.docker.com/linux/ubuntu bionic InRelease                                                                                                        
    Hit:6 http://ppa.launchpad.net/ondrej/php/ubuntu bionic InRelease                                                                                
    Hit:7 http://mirrors.digitalocean.com/ubuntu bionic InRelease                                  
    Hit:8 http://mirrors.digitalocean.com/ubuntu bionic-updates InRelease    
    Hit:9 http://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/6.0 Release  
    Hit:10 http://mirrors.digitalocean.com/ubuntu bionic-backports InRelease 
    Reading package lists... Done                      
    
    ## Run `sudo apt-get install -y nodejs` to install Node.js 16.x and npm
    ## You may also need development tools to build native addons:
         sudo apt-get install gcc g++ make
    ## To install the Yarn package manager, run:
         curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | gpg --dearmor | sudo tee /usr/share/keyrings/yarnkey.gpg >/dev/null
         echo "deb [signed-by=/usr/share/keyrings/yarnkey.gpg] https://dl.yarnpkg.com/debian stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
         sudo apt-get update && sudo apt-get install yarn
    
    
    root@nsn-do-lamp:~# sudo apt install -y nodejs
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    nodejs is already the newest version (16.17.0-1nodesource1).
    0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
    root@nsn-do-lamp:~# node -v
    v14.15.1
    
    
    root@nsn-do-lamp:~# npm  -v
    6.14.8



```What is wrong ? I restarted the OS but I have the same node 14.


How that could be fixed ?

---

### Post by &amp;KyT$0P# on 2022-09-02
Please post outputs from running the following commands in Terminal -
```
which -a node
apt-cache policy nodejs
```

Also, why are you logged in as root?  Normally in Ubuntu you log in as an administrator user, then use [FONT=Courier New]sudo[/FONT] to elevate to root.  Do you still get nodejs 14 if you're logged in as a non-root user?

---

### Post by nilovsergey on 2022-09-02
I got :

```
[FONT=monospace][COLOR=#000000]root@nsn-do-lamp:~# whoami[/COLOR]
root
root@nsn-do-lamp:~# which -a node
/usr/local/bin/node
/usr/bin/node
root@nsn-do-lamp:~# apt-cache policy nodejs
nodejs:
  Installed: 16.17.0-1nodesource1
  Candidate: 16.17.0-1nodesource1
  Version table:
 *** 16.17.0-1nodesource1 500
        500 https://deb.nodesource.com/node_16.x bionic/main amd64 Packages
        100 /var/lib/dpkg/status
     8.10.0~dfsg-2ubuntu0.4 500
        500 http://mirrors.digitalocean.com/ubuntu bionic-updates/universe amd64 Packages
     8.10.0~dfsg-2ubuntu0.2 500
        500 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages
     8.10.0~dfsg-2 500
        500 http://mirrors.digitalocean.com/ubuntu bionic/universe amd64 Packages
root@nsn-do-lamp:~# node -v
v14.15.1

[/FONT]
```

What can I try next ?

---

### Post by &amp;KyT$0P# on 2022-09-02
You could call NodeJS 16 by full path [FONT=Courier New]/usr/bin/node[/FONT]

Or if you no longer want the NodeJS 14 installation that's in [FONT=Courier New]/usr/local[/FONT] at all, you could try to uninstall it.  How to uninstall it would depend how it was installed.

---

### Post by nilovsergey on 2022-09-03
I suppose that I installed nodejs with commands :
```
cd ~
curl -sL https://deb.nodesource.com/setup_14.x -o nodesource_setup.sh
sudo bash nodesource_setup.sh
sudo apt install nodejs

```
So now I check :
```
root@nsn-do-lamp:~#  /usr/bin/node -v
v16.17.0
root@nsn-do-lamp:~# node -v
v14.15.1
root@nsn-do-lamp:~# whereis node
node: /usr/bin/node /usr/local/bin/node /usr/include/node /usr/share/man/man1/node.1.gz



```In which way have I to remove node 14 ?

---

### Post by nilovsergey on 2022-09-21
Could you please detalize how can I delete [COLOR=#000000]NodeJS 14 ? Which chacks have I to do?[/COLOR]

---

