---
title: "How can you install spesific Apache, PHP &amp; MySQL versions?"
date: 2012-12-13
forum: General Help
---

### Post by ThomThom on 2012-12-13
I want to replicate the setup of my website. Up until now I've used my windows machine with WAMP which is very easy to set up with specific Apache, PHP and MySQL versions.

But I wanted to create a virtual PC which I could easily transfer and clone etc. So I figured I'd install XUbuntu go from there.

Now, while searching for how to do this I find commands which just seem to pick the latest version.

```

sudo apt-get install apache2
sudo apt-get install mysql-server
sudo apt-get install php5
sudo apt-get install php5-mysql

```

etc etc.

But how do I pick and install exact versions?

---

### Post by Cheesemill on 2012-12-13
You don't.

When you install software from the repositories you always get the version that was current when your version of Xubuntu was released, but with bug fixes and security updates applied.

You could try downloading all of the required source code and compiling it yourself but you need to know ***exactly*** what you are doing. This also negates the advantages you get from using package management software (automatic updates, dependency resolution, known compatible software versions).

What versions of the software do you need?
There may be an Xubuntu release that is still supported that has close to the versions you require.

---

### Post by ThomThom on 2012-12-13
:( That does explain why I found so little info. My questions here usually ends up in compiling something... Might be that I have to bite the bullet on this one. ...or get a virtual Windows license, because it's a whole lot easier to install specific versions there.

```

Apache version 	2.2.23
PHP version 	5.2.17
MySQL version 	5.0.95-community

```

PHP version is a bit dated... :/

---

### Post by ThomThom on 2012-12-13
hmm... What about this SF topic: [http://serverfault.com/a/353562/116334](http://serverfault.com/a/353562/116334)

> 
You can install an older version of any package with Apt - you just have to look up the specific version name that you want. Assuming you're using Debian, you can look up old versions of packages at their site [http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

The format for installing said specific package is like this:

```
apt-get install <package name>=<version>
```

Such that if you want to install the version named 5.3.3-7+squeeze3, you use this:

```
apt-get install php5=5.3.3-7+squeeze3
```


Does this apply to XUbuntu?

---

### Post by Cheesemill on 2012-12-13
The Ubuntu release with the closest matching packages is probably 8.04 which would give you these versions:

Apache  2.2.8
MySQL   5.0.96
PHP5      5.2.4

The problem you would have with using 8.04 is that only the server version is still supported (command line only), also this support runs out in April.

I would agree with you that if you have to have those versions then you are probably better off with Windows.

---

### Post by ThomThom on 2012-12-13
The apt-get command in the SF topic won't work?

Was hoping to replicate current setup. Don't want to just jump into a newer versions before I know I can replicate the existing environment.

---

### Post by Cheesemill on 2012-12-13
> **ThomThom said:**
> The apt-get command in the SF topic won't work?

Highly unlikely, you'll end up in [dependency hell]("http://en.wikipedia.org/wiki/Dependency_hell").

Also some of the versions you are after simply don't exist in the Ubuntu repositories, for example the highest Apache version available is 2.2.22 (even in 13.04 which is still under development and hasn't been released yet).

Even if you could find the exact versions of the other packages they would be from different Ubuntu releases, meaning you would have to use repositories from more than one release. This is a sure fire way to break your system.

The easiest solution to all of this is to find out what OS your current host uses and install that.

---

### Post by ThomThom on 2012-12-13
Gotcha. I'm more concerned about the PHP version to be honest. I'll dig around and see what I end up with.

Thanks for the feedback.

---

