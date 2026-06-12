---
title: "Unable to install php5-curl"
date: 2014-08-29
forum: General Help
---

### Post by jason58 on 2014-08-29
Greetings!

On a current project I need to use Curl in php, but I'm having issues installing php5-curl. When I try
```
sudo apt-get install php5-curl
```
(with or without -f), I get:
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 php5-curl : Depends: php5-common (= 5.5.9+dfsg-1ubuntu4.3) but 5.5.10+dfsg-1+deb.sury.org~precise+1 is to be installed
E: Unable to correct problems, you have held broken packages.
```

I understand that it's saying that php5-curl wants a later version of php5-common to be installed.. but I'm not sure whether or I should try upgrading php5-common or do something else. Very open to suggestions as I really need this to work.

Thanks!

---

### Post by jason58 on 2014-08-29
To fix this I ended up adding the Ondrej PPA: [https://launchpad.net/~ondrej/+archive/ubuntu/php5](https://launchpad.net/~ondrej/+archive/ubuntu/php5)

In total:
```
sudo add-apt-repository ppa:ondrej/php5
sudo apt-get update
sudo apt-get install php5-curl
```

---

