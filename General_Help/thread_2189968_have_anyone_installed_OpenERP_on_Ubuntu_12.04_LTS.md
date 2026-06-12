---
title: "have anyone installed OpenERP on Ubuntu 12.04 LTS"
date: 2013-11-25
forum: General Help
---

### Post by miqdar-cmk on 2013-11-25
i want to ask, how to install OpenERP on Ubuntu 12.04 LTS with Offline Mode (not connect internet) ??
anyone can explain to me the way step by step
please

tks before

---

### Post by jdeca57 on 2013-11-25
Did you try step by step guides like [http://www.theopensourcerer.com/2012/12/how-to-install-openerp-7-0-on-ubuntu-12-04-lts/](http://www.theopensourcerer.com/2012/12/how-to-install-openerp-7-0-on-ubuntu-12-04-lts/) ?

---

### Post by SaFi2266 on 2014-02-23
OpenERP is probably the most well-known open-source ERP solution that exists today. With over 3000 modules, its capabilities are vast - and so are possible benefits it brings for businesses and organizations. Thanks to its release under the terms of GNU Affero General Public License (AGPLv3), OpenERP is free to use and share.

In this tutorial, we will show you how easy it is to have a running copy of OpenERP 7.0 (its latest stable release) in less than 15 minutes on a Debian/Ubuntu VPS. A minimal level of technical knowledge is all you need to get started!

Note: It is recommended to start with a freshly instantiated VPS in order to prevent any possible issues, due to the large amount of OpenERP dependencies. Do not forget to update and upgrade your system's default software packages with the following commands after logging on:

```

sudo apt-get update
sudo apt-get upgrade

```

We will be using a pre-packaged version of the application to install it on our system. This makes things infinitely easier, as it is going to install all the dependencies and set them up correctly to work with OpenERP, thus producing us a clean copy.

Let's start with adding the download URL (address) to the aptitude repository sources:

```

echo "deb http://nightly.openerp.com/7.0/nightly/deb/ ./" >> /etc/apt/sources.list

```

Afterwards, we need to update the list:

```

sudo apt-get update

```

Now we are ready to download and install OpenERP and its dependencies!

**Note:** The OpenERP package itself is not signed, and a cryptographic key is not provided. Therefore, apt will warn you that it can not be authenticated, requesting you to install it without verification.

After entering the command below, you will be asked to confirm:

[LIST]
[*]The list of packages that are going to be downloaded and installed;
[*]The amount of disk space that will be used;
[*]And that the openerp package is authentic.
[/LIST]

In order to install, run the following:

```
sudo apt-get install openerp
```

wait setup to finish
Enter the following URL to your browser, replacing it with your server's IP address:

```
http://your_vps_ip_address:8069
```

that's all

original post submitted by  [O.S. Tezer]("https://twitter.com/ostezer") with more details [here]("https://www.digitalocean.com/community/articles/how-to-install-and-set-up-openerp-7-0-on-a-debian-7-ubuntu-13-10-vps")

---

