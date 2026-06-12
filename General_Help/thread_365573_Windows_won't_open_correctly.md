---
title: "Windows won't open correctly"
date: 2007-02-19
forum: General Help
---

### Post by wej1971 on 2007-02-19
This is a weird one. I'm currently getting prompted for an admin user password whenever I open things (users and groups, network stuff etc) despite the fact that I've always been able to open these things before without a root password. What's more, sometimes (quite often in fact) the windows don't open fully, with a blank window in a hung state that I have to kill.

Any ideas?

---

### Post by wej1971 on 2007-02-19
Just as an additional note, when I first get into KDE I'm prompted twice for an administrative user and then two users and groups windows appear (this is every time I've booted up despite closing them the previous time). In addition, when I shut down I get a message about not having administrative privileges and then synaptic package manager is visible open behind the dialog box just before shutdown.

---

### Post by lhtown on 2007-02-19
Have you enabled root? (Not really recommended for most people) It sounds to me like you were running Ubuntu as root before since networking and changing user permissions normally require root permissions.

---

### Post by wej1971 on 2007-02-20
No, this is something weird - I've not changed anything and all of a sudden I get prompted for a root password when I do anything, and some windows freeze on opening even when a root password is supplied. If I user management is used within KDE and I click the administration mode button the whole thing just freezes up - I'm not even prompted for a password.

---

### Post by wej1971 on 2007-02-20
Anybody know what's going on? I'm having to type an administrative password for half the things I have to open (and wasn't prompted to before) and some windows like users and groups and networking just freeze when the windows opens.

Is there any way to repair from console as I'm completely stuffed at the moment!

---

### Post by lhtown on 2007-02-20
Maybe you should check to see if you've been "owned" or infested with a rootkit.

Unless you have been seriously messing with your users and permissions, it sounds like you should consider the possibility that maybe someone has been playing around on your computer either locally or remotely.

---

### Post by wej1971 on 2007-02-21
I suppose it's possible, but given that there is no-one locally and my internet connection has been on for less than an hour in the last week, I'm not sure how.

Is there anyway to determine whether this is the case?

---

### Post by lhtown on 2007-02-22
I don't know what is going on, but from my understanding, a rootkit could have been installed long ago and lay dormant or at least be left without the user noticing anything unusual.

Rootkits are a fairly rare phenomenon with Ubuntu, but they do happen from time to time.

Also, remember that it is important to use non-obvious/difficult to crack and guess passwords.

---

### Post by wej1971 on 2007-02-23
Trouble is Linux has been installed less than two weeks and has only been networked for a few hours in that time.

---

