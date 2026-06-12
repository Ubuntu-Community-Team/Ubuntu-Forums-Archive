---
title: "how to disable ubuntu authentication"
date: 2014-07-08
forum: General Help
---

### Post by christon74 on 2014-07-08
Good morning all ubunters :)
I am the only person home to use computers. I have absolutely no need for Password and I am really tired of typing my password each time I log on to Ubuntu. 
I have found this method (but it does not work)
Log into Ubuntu and open your Terminal program.
    
 
 sudo nano /etc/sshd_ config
Press Ctrl W to open search window and type 'PasswordAuthentication' then press Enter
Remove the # at the start of the PasswordAuthentication then replace 'Yes' with 'No'
Save file and restart.

Problem: each time I press CtrlW and type 'PasswordAuthentication' I get 'PasswordAuthentication' not found!!!!!!!!

:confused::shock::frown:

Thank you in advance for any tip. 

Have a nice Tuesday. 

Chris.

---

### Post by claracc on 2014-07-08
What ubuntu do you have? 12.04 ?, 14.04?

I have ubuntu 12.04 and there is not any /etc/sshd_config file but a /etc/ssh/ssh_config file where there is a commented line with PasswordAuthentication . What you are trying is a way to share files in a network withou password. and the sshd_config file is the server one. I suppose you are following this: [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring) which parent page is [https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking)

So , I think you are trying to do a thing which is not related with what you want: not to have a password for your user account at login, which I think it is impossible (as far as I know). You need a password to authenticate in order to do certain things which only root can do.

---

### Post by coffeecat on 2014-07-08
If you simply want to avoid typing in your password at login, all you have to do is:

Click on the cogwheel icon top right -> System Settings -> User Accounts -> highlight your account -> Unlock -> switch "Automatic Login" to on. Assuming, that is, that you are running 14.04.

If you want to avoid a password prompt when doing things that require administrative authorisation after logging in, I for one am not going to tell you how. You don't have to authorise things very often and it is a useful reminder to help you not to break your system or do something unwise in an absent-minded moment. And as claracc has pointed out, the ssh howto you have come across is irrelevant to your described needs.

---

### Post by brw2 on 2014-07-08
I'm not sure why you are editing the SSH daemon's configuration.  The change you are trying to implement would enable key based login via SSH, not bypassing the password at the login screen.

---

