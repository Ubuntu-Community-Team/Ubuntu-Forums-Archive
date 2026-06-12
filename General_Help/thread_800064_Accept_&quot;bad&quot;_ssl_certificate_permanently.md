---
title: "Accept &quot;bad&quot; ssl certificate permanently with evolution"
date: 2008-05-19
forum: General Help
---

### Post by Zxaos on 2008-05-19
Hi,

I'm trying to get evolution working, and the host I'm connecting to uses a self-signed SSL certificate.  I can accept this certificate and the connection works, but when evolution is closed and then re-opened, I am re-prompted about accepting the "bad" certificate.

Is there any way to accept this permanently? The searching that I've done seems to indicate I have to import the certificate by hand - but I don't know how to extract the certificate from evolution to do that!

If someone could help with this, I'd really appreciate it.

---

### Post by yaztromo on 2008-08-15
Seconding this request!

---

### Post by techstop on 2008-08-15
Erm, thirding?

I've been wondering about this very thing for quite some time. Maybe it needs a feature request?

EDIT: OK, I just figured it out, it's pretty straight-forward in the end...

Open your web hosting site using https in firefox (I used my https webmail).
Double-click on the padlock icon in the status bar at the bottom of the window.
Click on the security tab.
Click view certificate.
Click details.
Click export.
Save as an X.509 Certificate (first option).
Open Evolution.
Edit>Preferences>Certficates
Click Import
Browse to the certificate you just saved, click Open
You're done!

EDIT #2:
I spoke too soon. That procedure successfully imports the certificate as a trusted authority, but I still get a prompt from evolution, presumably because the certificate name for the shared server doesn't match my mail server name. Back to square 1 I'm afraid...

---

### Post by aselvan on 2008-09-09
Is there any solution at all for this problem?. I changed the certificate on my server side i.e. postfix/dovecot to use my own valid certificate instead of the default snakeoil certificates, but still no go. 

Seem like this is the problem with evolution and its been there for a long time but yet no one seem to know of a good solution. It is really annoying to enter OK everytime you start evolution!.

---

### Post by nickpj on 2008-09-10
I'll just add "me too", and more usefully, that I have logged this upstream at: [http://bugzilla.gnome.org/show_bug.cgi?id=551607](http://bugzilla.gnome.org/show_bug.cgi?id=551607)
For that feature request, I just used the steps given in this forum, since they exactly match the steps that I tried - hope that's okay!

-- All the best,
Nick.

---

### Post by yaztromo on 2008-09-10
You have to create a self-signed certificate for your dovecot server with the correct server name then export it using ssl and import it into your evolution. I have evolution and dovecot talking fine on a network here using TLS with no prompts.

It's been sometime since I got it all going but I'll try and figure out the actual steps again when I get a spare moment.

---

### Post by techstop on 2008-09-10
> **yaztromo said:**
> You have to create a self-signed certificate for your dovecot server with the correct server name then export it using ssl and import it into your evolution. I have evolution and dovecot talking fine on a network here using TLS with no prompts.

It's been sometime since I got it all going but I'll try and figure out the actual steps again when I get a spare moment.

This is not a solution for people on shared web hosting though. Generally a self-signed certificate is created by the web host with a generic server name, and then all the accounts on the server use the one certificate. In that scenario, the certificate name will never match the server name.

So, you can get Evolution to trust a self-signed certificate authority, but it seems you can't get it to ignore name mis-matches.

---

### Post by yaztromo on 2008-09-15
Ah I see. Do you not have access to the server yourself?

---

### Post by the real omni on 2008-09-28
bump

Add me to the list of people who would like this problem solved but don't have an https:// webmail page to export a cert from...

Help! :|

---

### Post by olyd on 2009-10-07
Looks like this topic is a bit dead, but here a suggestion anyway:

Try:
  openssl s_client -connect [host]:[port] -showcerts

to grab the certificate and paste it into a file, and then import it into Evolution.

---

