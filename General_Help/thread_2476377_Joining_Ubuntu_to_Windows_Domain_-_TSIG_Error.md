---
title: "Joining Ubuntu to Windows Domain - TSIG Error"
date: 2022-06-24
forum: General Help
---

### Post by julian-ecs on 2022-06-24
[COLOR=#333333][FONT=&amp]Hello,[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]I am new to Linux / Ubuntu so please keep answers quite simple![/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]I am testing adding Ubuntu (20 and now 22) machines to a company windows domain. I am setting up the machines with Linux then manually adding to the domain.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]This looks to be going quite well but have a apparent issue.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]I have got as far as editing mkhome and doing a sudo pam-auth-update and that is all fine. I then do:[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]sudo systemctl restart sssd  - that looks to have worked[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]I then:[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]systemctl status sssd - this is where the problem occurs, it get a file that includes:[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]*****.***.local systemd[1]: Started System Security Services Daemon.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]*****.***.local sssd[16088]: ; TSIG error with server: tsig verify failure
[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]*****.***.local sssd[16088]: update failed: REFUSED
*****.***.local sssd[16088]: ; TSIG error with server: tsig verify failure
*****.***.local sssd[16088]: update failed: REFUSED
*****.***.local sssd[16088]: ; TSIG error with server: tsig verify failure
*****.***.local sssd[16088]: update failed: REFUSED
[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]If I ignore these TSIG errors and continue the machine appears to work OK on the domain - I can log on as a domain user, log onto sharepoint, open shared drives, install McAfee EPO agent and it communicates with the on prem EPO server etc.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]What does the TSIG error mean? How do I fix it? Does it matter?
I have followed:[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp][https://computingforgeeks.com/join-ubuntu-debian-to-active-directory-ad-domain/](https://computingforgeeks.com/join-ubuntu-debian-to-active-directory-ad-domain/)[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]I have not touched  /etc/samba/smb.conf - should I do so and will it help, if so what do I need to change?

Thanks,[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Julian[/FONT][/COLOR]

---

