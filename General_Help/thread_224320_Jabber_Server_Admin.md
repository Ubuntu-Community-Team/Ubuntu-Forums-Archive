---
title: "Jabber Server Admin"
date: 2006-07-27
forum: General Help
---

### Post by Elrohir on 2006-07-27
guys, I got a new challenge here...

I'm on a project on IM Servers and I just installed jabberd2 from repositories... how do I administer the service? how do I create new users?

please! i need ASAP help on this one...

---

### Post by dtfinch on 2006-07-29
There's always the documentation: [http://jabberd.jabberstudio.org/2/docs/](http://jabberd.jabberstudio.org/2/docs/)

Quote: "At the time of writing, there are no scripts for adding users; however, users can be added easily to a MySQL or PostgreSQL database."

Enabling public registration would allow users to allow themselves.

I think I got jabberd2 working once, or maybe it was ejabberd, or both. I know I tried several. Eventually I started using one written in Java called WildFire (previously known as Jive Messenger) which has worked out very well, and is easy to administer.

---

### Post by doogy2004 on 2006-09-14
WildFire is definately the way to go, it has many options and settings, and it will work great right out of the box.  The tricky part is that it does not install itself as a service in init.d It comes with a template script to help out, the template script was intended for Redhat, but it doesn't take much to work in Ubuntu, just read the comments in the script.

---

### Post by jethro10 on 2006-12-01
Even easier to start it as a daemon on 6.06 LTS

Copy the wildfired script from /opt/wildfire/bin/extra to /etc/init.d
and then run:
sudo update-rc.d wildfired defaults


the manual start | stop works as well

I would agree, wildfire is a perfectly easy choice.

---

### Post by doogy2004 on 2006-12-03
> **jethro10 said:**
> Even easier to start it as a daemon on 6.06 LTS

Copy the wildfired script from /opt/wildfire/bin/extra to /etc/init.d
and then run:
sudo update-rc.d wildfired defaults


the manual start | stop works as well

I would agree, wildfire is a perfectly easy choice.

Does the script need to be changed to run as daemon at startup?
I was under the understanding that it needed to be changed.

It would be great if it was golden with out needing to be changed.

---

