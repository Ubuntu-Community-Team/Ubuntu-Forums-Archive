---
title: "Thunderbird keeps saying my password is incorrect"
date: 2016-07-12
forum: General Help
---

### Post by pedro_rodriguez2 on 2016-07-12
I thought I would try Thunderbird. It seems to have a problem with my email password. It just keeps asking for the password, I enter it correctly, but it can't log in. I tried various settings but then Thunderbird tells me 'this setting is not correct for this server' or something like that, so I go back to 'normal password'.

My name, as seen in my email is Pedroski. I don't know if that is important, but when I was setting up the Thunderbird account, it also told me the name was wrong.

Please see the attached thumbnail for a peek at the problem.

---

### Post by Rex Bouwense on 2016-07-12
Before you completely dump Thunderbird there are a few things to check.  
1.  Make sure that your caps lock is not engaged.  I know it sounds simple but it has happened to me so I always suggest it.
2.  Second log into your email provider (gmail, yahoo, hotmail, etc) with your user name and password though your browser  That will make sure that you are using the correct user name and password.
3.  Open Thunderbird and check your account settings (under edit).  When you initially set up Thunderbird you were asked for your name, your email address, and your password.  If you checked remember password you will not be asked for it every time you open Thunderbird.  That is the password that it is asking you for (not your log in password)  If you have forgotten what you put down as a password then you could always delete the account and then add it later.  That password if you change it must be changed with your email provider.

---

### Post by jeremy31 on 2016-07-12
Are you using gmail?  There are times when gmail flags a new login as suspicious and requires confirmation from a device already logged in

---

### Post by pedro_rodriguez2 on 2016-07-12
Thanks!
I am definitely using the correct password. I have to log in with it every day, it is long and complicated, but I don't get it wrong.
I have checked the account settings.

I don't quite understand. My log in password is NOT my email login password?? How does that work? I unclicked 'remember password'.

Here is another screenshot. I junked that account in Thunderbird, closed Thunderbird down, restarted it. Made a new account. Still same old 'Password incorrect' 

You can see from the thumbnail I attached in my first post, that the mail server is imap.qq.com

qq is very popular in China and gmail is unreachable without a vpn.

Added another screenshot of manual config in Thunderbird.

---

### Post by deadflowr on 2016-07-12
You need to check the settings in the email's web page to see that the settings there are correct and allow you to export those settings to thunderbird.

---

### Post by pedro_rodriguez2 on 2016-07-13
Haha, you were right. I had to go to settings in the email page, then click the account tab, then click open imap/smtp.

They  then open a window. In that window is a message and a phone number. I  had to send that message to that phone number. Then I got a 4 block set  of letters, like a credit card number, but all letters.

That is what Thunderbird needed to log in to the imap server. Apparently it does not need my email password!

The fact that it is all in Chinese slowed me down a bit!

---

