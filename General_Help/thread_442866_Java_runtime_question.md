---
title: "Java runtime question"
date: 2007-05-13
forum: General Help
---

### Post by ed67 on 2007-05-13
I use Logmein.com to access my office pc running windows xp home.  It works in Firefox in windows, but does not work in firefox in ubuntu.  Firefox wants a java runtime environment plugin.

I went to synaptics and installed what appears to be a java runtime environment.  Now, firefox no longer asks for the JRE plugin, but an error pops up just before connection is complete.  It says SSL Peer Unverified Exception: peer not verified.

Any help would be appreciated.  I'm completely new to Ubuntu and Linux.

---

### Post by canadianwriterman on 2007-05-14
There's also a mozilla-plugin for Java. It should be in synaptics, just below the jre environment.

---

### Post by geekphreak on 2007-05-14
I would also recommend you install sun-java6 packages and use that instead of the default gnu java distribution. There may be some incompatibilities there so you may want to make sure you have the latest packages. That's my 2Hz.

---

### Post by zvacet on 2007-05-14
[http://www.java.com/en/download/help/5000010500.xml]("http://www.java.com/en/download/help/5000010500.xml")

Scroll to the bottom of the page and you will find instructions for java plugin install.

---

### Post by ed67 on 2007-05-14
OK I'm with you on this.  I follow the directions carefully.  I don't seem to have permission to access the root.  I don't see how as I'm the only person who uses this computer, I installed Ubuntu, etc. but in any case I don't know the root password.

So the next step was to use directories where I DO have permission.  I followed those steps, terminal seems to be OK with the stuff I typed in, but instead of associtating the two directories (firefox plugins and my java one) it says Permission Denied.

How can I give it permission?  I have permission to read and write here because I do it all the time.  I know the password if I just knew where to type it in.

Thanks again.

---

### Post by geekphreak on 2007-05-14
Type in > sudo su -, then your password, and you should become root. Then proceed with instructions.

---

### Post by ed67 on 2007-05-14
That worked as far as getting it to accept what I was doing.  Unfortunately it didn't help anything.  The same error still pops up that I listed before.  I think it has something to do with it asking me if I want to run the applet from this site (a long site url that is basically logmein.com) and should it "whitelist" the app.

I think I'm gaining, at least in knowledge so thanks for all your help.  Let me know what you think now.

---

