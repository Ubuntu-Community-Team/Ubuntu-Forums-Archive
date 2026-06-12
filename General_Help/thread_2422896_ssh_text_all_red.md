---
title: "ssh text all red"
date: 2019-07-14
forum: General Help
---

### Post by sniper8752 on 2019-07-14
When I ssh into my ubuntu server, the text is all red.  Is there any way to change this so it uses the default color scheme?

---

### Post by &amp;KyT$0P# on 2019-07-14
Does this red color persist in the terminal after you exit the ssh session?  As in, are subsequent things you do in that terminal colored in red as well?

Please post the output from running this command on your Ubuntu server -
```
cat ~/.bashrc
```
(assuming you use bash as your shell on your server when you ssh into it)

If you have your server set up to display a custom "message of the day" when you ssh into it, maybe also check that for an unclosed red color tag?

---

### Post by HermanAB on 2019-07-15
Some systems will colour the text red when you are logged in as root.

---

### Post by sniper8752 on 2019-08-24
> **halogen2 said:**
> Does this red color persist in the terminal after you exit the ssh session?  As in, are subsequent things you do in that terminal colored in red as well?

Please post the output from running this command on your Ubuntu server -
```
cat ~/.bashrc
```
(assuming you use bash as your shell on your server when you ssh into it)

If you have your server set up to display a custom "message of the day" when you ssh into it, maybe also check that for an unclosed red color tag?
It does not.
It says that the file does not exist.

---

