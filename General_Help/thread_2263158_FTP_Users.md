---
title: "FTP Users"
date: 2015-01-29
forum: General Help
---

### Post by patrickfrog on 2015-01-29
Hi everyone,

I am in need of some advice on a project I am beginning.  As a brief overview, I am developing a website where users sign up for accounts.  These accounts correspond to streams that the users have and control.  At the moment, these users are set up manually as FTP folders and the appropriate directory structure is created for them.  This process needs to be automated for ease of use.  My idea is create a new linux user for each person who creates an account which then has an FTP account associated to it which allows users to upload to their home directories.

What I need:
[LIST]
[*]The ability to dynamically create new users with their own permissions from a webpage
[*]A new FTP account (that corresponds to this user) to be created
[*]The ability for the user to log in on the web page to upload files to thier FTP folder and manage other aspect of their "account"
[/LIST]

I guess these quastions can be divided into a few key categories.  First off, is there a secure way to accomplish these tasks?  Second, is there a better way to go about this other than creating linux users (which I thought would be the easiest to manage)?  Third, and more of a web developer question, I need the user to be able to log in on the website which in turn allows the user to upload (through a web/PHP based uploader) files to the respective account.  I am not sure how to implement this sort of behavior in a web-based environment.

Thank you in advance for any advice you can give me.  I'm not looking for an eniter solution to be presented to me, I simply need some ideas and advice on haow I could go about implementing my though process.  Also, any added advice on how to make this as secure as possible is greatly appreciated.

Patrick

---

### Post by HermanAB on 2015-01-30
By default, out of the box, proftpd and vsftpd allow users to access their home directory.  So you need not do anything.

---

