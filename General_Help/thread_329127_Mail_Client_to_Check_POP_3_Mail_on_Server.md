---
title: "Mail Client to Check POP 3 Mail on Server?"
date: 2007-01-01
forum: General Help
---

### Post by fiestaforever on 2007-01-01
Hi, 

does anone know a (GUI) client that is able to check mail on a POP3 server without downloading the complete messages (to sort out and delete spam or large messages on the server)? Thunderbird or Balsa can't do that.
 
Examples for this functionality in Windows: The Bat ("mail dispatcher"), Magic Mail Monitor, Mailwasher.

---

### Post by carla on 2007-02-06
mailcheck: [http://packages.ubuntu.com/edgy/mail/mailcheck](http://packages.ubuntu.com/edgy/mail/mailcheck)
pop3browser: [http://packages.ubuntu.com/edgy/mail/pop3browser](http://packages.ubuntu.com/edgy/mail/pop3browser)

---

### Post by jllortega on 2007-02-10
I found this topic looking for the some kind of software as in the original post. I installed the both mailcheck and pop3browser from the repository, but they were not added to any menu. So I am trying to run them without success either from the terminal or by creating a launcher. 

Any suggestions?

---

### Post by labinnsw on 2008-04-27
I am sure that by now fiestaforever must have moved on, but I am a persistent .... So, I spent the last year trying to find something like "Mailbox Dispatcher" for linux and in particular Ubuntu. I have looked at Pop3browser a number of times but finally figured it out today. What a wonderful anti-spam tool. It is in fact quicker than "Mailbox Dispatcher" (which I love, if only I was still using Windows). Enough of the long argument heres how to get going and by the way this works on ADSL2 so it is not only for dial up or low bandwidth.

Follow the steps below to set up and use this great anti spam tool.


Omit the double quotes in all instructions

[SIZE="4"]Installation[/SIZE]

1 Go to: System>>Administration>>Synaptic
2 Search for pop3browser
3 Mark it for installation and select "Apply"

[SIZE="4"]Configure[/SIZE]

1 Open a terminal: Applications>>Accessories>>Terminal
2 Type "gedit ~/.pop3browserrc"
3 Type your information in the text editor
e.g. 
pop.mail.yahoo.com	username1	password1
mail.tpg.com.au	username2	password2

4 Save and close the file

[SIZE="4"]Check Your Mail[/SIZE]

1 In the still open terminal type: "pop3browser"
2 At the next line type "login 0" to log in to the first account
3 Type "m" to see a list of mail in your account
3 Type "d 1-3" to delete the first 3 messages (only if you want them deleted!)
4 Type "c" to delete the marked messages and close that account.
5 Repeat steps 1-4 for your other accounts using next "login 1", "login 2" etc.
6 Type "exit" to close the program.

[SIZE="4"]To see other possible commands type "help" at any stage while using pop3browser[/SIZE]

---

