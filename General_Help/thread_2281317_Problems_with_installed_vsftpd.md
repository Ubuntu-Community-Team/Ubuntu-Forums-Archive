---
title: "Problems with installed vsftpd"
date: 2015-06-06
forum: General Help
---

### Post by Christoph_Waninger on 2015-06-06
Good morning,

Using: vServer - Ubuntu 14.04
Problem: vsftpd

at the moment i am having some problems with my FTP-server (kinda strange huh?). Until today i had many ftps running without any issues but now i need some advice.

i installed the vsftpd without any problems and started to do some configuring. Then i wanted to restart the vsftpd service and i get the message "unknown instance". I were searching in the Internet for any workarrounds but i could only find on solution saying "just reinstall your vsftp and it should be running again". I reinstalled like 5 times and still having the same issue. It seems like it does not finish the install or something.

Well this was problem one (the ftp is still running normally). The second problem is that i cant jail a ftp user to the directory indicated. So he will start in that folder but an just cd until he sees the real root folder on my server. I tried many tutorials to jail a user

> 


[LIST]
[*]Create user with useradd [user_name].
[*]Create user's password with passwd [user_name]. (You'll be prompted to specify the password).
[*]Create FTP directory in /var/ftp and then bind to the 'home' directory you wish to specify for this user with mount --bind /var/www/vhosts/domain.com/ /var/ftp/custom_name/.
[*]Change user's home directory with usermod -d /var/ftp/custom_name/ user_name
In /etc/vsftpd/vsftpd.conf, ensure all all of the following are set:-

[LIST]
[*]chroot_local_user=YES
[*]chroot_list_enable=YES
[*]chroot_list_file=/etc/vsftpd.chroot_list
[/LIST]
[/LIST]
[FONT=Helvetica Neue]Only list users in the vsftpd.chroot_list file if you want them to have full access to anywhere on the server. By not listing them in this file, you're saying restrict all vsftpd users to their specified home directory.[/FONT]
[FONT=Helvetica Neue]In other words (for reference):-[/FONT]

[LIST=1]
[*]means that by default, ALL users get chrooted except users in the file...
[LIST]
[*]chroot_local_user=YES
[*]chroot_list_enable=YES
[/LIST]

[*]means that by default, ONLY users in the file get chrooted...
[LIST]
[*]chroot_local_user=NO
[*]chroot_list_enable=YES
[/LIST]
[/LIST]



This were my last intend i found from serverfault.com - even with this mounting stuff i cant really jail the user to a specific directory.
 
Would be glad if anyone could help me - first of all of the problem with unknown service, since i am not sure if the daemon is restarting corectly and need to restart the whole server all the time.

Thanks in advance :)

---

### Post by dino99 on 2015-06-06
is it installed from the 14.04 archive or from an external source ?
[https://help.ubuntu.com/community/vsftpd](https://help.ubuntu.com/community/vsftpd)

---

### Post by Christoph_Waninger on 2015-06-06
I installed the vsftpd with the apt-get install vsftpd mode - so i guess it should be alright - u guess it would be diffrent if i install it via wget the file and install it that way?

Regards,

---

