---
title: "setback when installing rvm"
date: 2014-06-22
forum: General Help
---

### Post by aviv2 on 2014-06-22
i m trying to install rvm to be able to run Beef, 
i have tried this:

bash -s stable < <(curl -s [https://raw.githubusercontent.com/wayneeseguin/rvm/master/binscripts/rvm-installer](https://raw.githubusercontent.com/wayneeseguin/rvm/master/binscripts/rvm-installer)) source ~/.bash_profile
rvm install 1.9.3-p0 --with-gcc=clang
rvm use 1.9.3

and i got:

```
Error running 'requirements_debian_update_system ruby-1.9.3-p0',
showing last 15 lines of /home/avivfl/.rvm/log/1403403654_ruby-1.9.3-p0/update_system.log
++ case "${TERM:-dumb}" in
++ case "$1" in
++ [[ -t 2 ]]
++ return 1
++ printf %b 'There has been error while updating '\''apt-get'\'', please give it some time and try again later.
For 404 errors check your sources configured in:
    /etc/apt/sources.list
    /etc/apt/sources.list.d/*.list
\n'
There has been error while updating 'apt-get', please give it some time and try again later.
For 404 errors check your sources configured in:
    /etc/apt/sources.list
    /etc/apt/sources.list.d/*.list
++ return 100
Requirements installation failed with status: 100.


```


i have tried either:

rvm get head
rvm reload
rvm install 1.9.3-p194
rvm use 1.9.3

and got:

```
Error running 'requirements_debian_update_system ruby-1.9.3-p194',
showing last 15 lines of /home/avivfl/.rvm/log/1403403795_ruby-1.9.3-p194/update_system.log
++ case "${TERM:-dumb}" in
++ case "$1" in
++ [[ -t 2 ]]
++ return 1
++ printf %b 'There has been error while updating '\''apt-get'\'', please give it some time and try again later.
For 404 errors check your sources configured in:
    /etc/apt/sources.list
    /etc/apt/sources.list.d/*.list
\n'
There has been error while updating 'apt-get', please give it some time and try again later.
For 404 errors check your sources configured in:
    /etc/apt/sources.list
    /etc/apt/sources.list.d/*.list
++ return 100
Requirements installation failed with status: 100.
avivfl@ubuntu:~$ suto tail -f /home/avivfl/.rvm/log/1403403795_ruby-1.9.3-p194/update_system.log
No command 'suto' found, did you mean:
 Command 'sumo' from package 'sumo' (universe)
 Command 'sudo' from package 'sudo-ldap' (universe)
 Command 'sudo' from package 'sudo' (main)
 Command 'uuto' from package 'uucp' (universe)
suto: command not found
avivfl@ubuntu:~$ sudo tail -f /home/avivfl/.rvm/log/1403403795_ruby-1.9.3-p194/update_system.log
For 404 errors check your sources configured in:
    /etc/apt/sources.list
    /etc/apt/sources.list.d/*.list
\n'
There has been error while updating 'apt-get', please give it some time and try again later.
For 404 errors check your sources configured in:
    /etc/apt/sources.list
    /etc/apt/sources.list.d/*.list
++ return 100
    /etc/apt/sources.list
    /etc/apt/sources.list.d/*.list
\n'
There has been error while updating 'apt-get', please give it some time and try again later.
For 404 errors check your sources configured in:
    /etc/apt/sources.list
    /etc/apt/sources.list.d/*.list
^Cavivfl@ubuntu:~$ Error running 'requirements_debian_update_system ruby-1.9.3-p0',
showing last 15 lines of /home/avivfl/.rvm/log/1403403654_ruby-1.9.3-p0/update_system.log
++ case "${TERM:-dumb}" in
++ case "$1" in
++ [[ -t 2 ]]
++ return 1
++ printf %b 'There has been error while updating '\''apt-get'\'', please give it some time and try again later.
For 404 errors check your sources configured in:
    /etc/apt/sources.list
    /etc/apt/sources.list.d/*.list
\n'
There has been error while updating 'apt-get', please give it some time and try again later.
For 404 errors check your sources configured in:
    /etc/apt/sources.list
    /etc/apt/sources.list.d/*.list
++ return 100
Requirements installation failed with status: 100.


```


any ideas why? 10x

---

### Post by anakai on 2014-06-22
Do you have all the dependencies for Ruby installed?

```
sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties
```

---

### Post by aviv2 on 2014-06-22
same errors bro...

---

### Post by oldos2er on 2014-06-22
Moved to General Help.

---

