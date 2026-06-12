---
title: "azureus not working"
date: 2007-03-09
forum: General Help
---

### Post by greeneggsnsam on 2007-03-09
whenever i open azureus it closes straight away- any help?

---

### Post by Gannin on 2007-03-09
Are you running it from an icon or from the terminal?

---

### Post by YoG%*@ on 2007-03-09
hi

can you start azureus from a terminal and then post the error message(s), if any?

greetz, 
mux

---

### Post by morpheus01 on 2007-03-10
Local Time = Sat Mar 10 13:08:49 2007
Elapsed Time = 4
#
# The exception above was detected in native code outside the VM
#
# Java VM: Java HotSpot(TM) Client VM (Blackdown-1.4.2-02 mixed mode)
#
# An error report file has been saved as hs_err_pid11802.log.
# Please refer to the file for further information.
#
Aborted (core dumped)


Am getting this since the last nights update.
It was working before after downloading the .jar file and moving it to the Azureus folder. Any ideas?

sudo mv /home/ivan/Desktop/Azureus2.5.0.4.jar .

---

### Post by Biggus on 2007-03-10
Dude, I used to get this all the time (still do now and then), and I 'solved' it by deleting some log files I think out of a folder somewhere, (presumable wherever Azureus stores log files)

If I can find it again (it usually takes me half an hour to work out if its /etc or /var I'm looking for) I'l try to be a little bit more specific.

---

### Post by morpheus01 on 2007-03-10
> **Biggus said:**
> Dude, I used to get this all the time (still do now and then), and I 'solved' it by deleting some log files I think out of a folder somewhere, (presumable wherever Azureus stores log files)

If I can find it again (it usually takes me half an hour to work out if its /etc or /var I'm looking for) I'l try to be a little bit more specific.

Thank you Biggus. That'd be great, if you find out where they are.

---

### Post by Biggus on 2007-03-10
Yeah I remember now, they're sneaky folders, actually in your home directory, and they start with a . (period) , so as to confuse recently converted windoze users such as I.

Anyhow, the folder I am in is called

/home/yourusername/.azureus/

and I generally delete the files called

hs_err_pid_12345.log (and all similar ones)

and also anything which is actually in the /logs/ folder too.

Works for me, but I can't explain why.

---

### Post by thesoothsayer on 2007-03-11
Hi,

I'm new to Ubuntu and this is my first post. Anyway, I had a similar problem after installing Eclipse this morning. It was working fine before that.

My solution was:
1. sudo update-alternatives --config java
2. change it to the java-gcj option
3. start Azureus (it should start now)
4. exit Azureus
5. sudo update-alternatives --config java
6. change it back to the Sun jre
7. start Azureus again

Hope this works for you.

---

### Post by MidKnight on 2007-03-11
I had the same problem right after installing it, but Biggus' fix worked for me.
That is...for a moment. The program quit suddenly while I was choosing a destination folder.
thesoothsayer's seems fine though

---

### Post by morpheus01 on 2007-03-11
> **thesoothsayer said:**
> Hi,

I'm new to Ubuntu and this is my first post. Anyway, I had a similar problem after installing Eclipse this morning. It was working fine before that.

My solution was:
1. sudo update-alternatives --config java
2. change it to the java-gcj option
3. start Azureus (it should start now)
4. exit Azureus
5. sudo update-alternatives --config java
6. change it back to the Sun jre
7. start Azureus again

Hope this works for you.

Thanks for this,
Don't know why but this worked - I didn't have a gci option, but there was a Java wrapper (I assume it must be some sort of wrapper script) option which did the trick. 
The Sun jre one didn't work after the restart.

---

