---
title: "Getting logged out after login + “Signature not found in user keyring” (16.04.3 LTS)"
date: 2018-04-26
forum: General Help
---

### Post by hellouniverse on 2018-04-26
[COLOR=#111111][FONT=Ubuntu]Dear Ubuntu community,

I got two problems. As I don't know if they are connected I will describe both:[/FONT][/COLOR]

[LIST=1]
[*]After I login I keep **getting logged out** after a few seconds.
[*]I **can't access** my **user data** as I am getting "Signature not found in user keyring. Perhaps try the interactive 'ecryptfs-mount-private'"
[/LIST]
[COLOR=#111111][FONT=Ubuntu]Cause I forgot my user password I followed [this guide]("http://www.psychocats.net/ubuntu/resetpassword") to reset it with root user.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Before I had been able to login at all I struggled with a login loop I was able to "solve" with [this solution]("https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop") by setting right user rights for **.Xauthority** and **.ICEauthority**.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]This is the output I am getting right now logging in with terminal:

[/FONT][/COLOR][IMG]https://i.imgur.com/UTDsODI.jpg[/IMG][COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I noticed the message "Signature not found in user keyring. Perhaps try the interactive 'ecryptfs-mount-private'". So I tried the suggested command resulting in an "unwrapping passphrase and inserting into the user session keyring failed 5" error:
[/FONT][/COLOR][IMG]https://i.imgur.com/6zNpdqL.jpg[/IMG][COLOR=#111111][FONT=Ubuntu]

 I think this is the reason why I can't see my private data after login:
[/FONT][/COLOR][IMG]https://i.imgur.com/X5zQjIw.jpg[/IMG]


[B]_Some more logs:_

[B].xsession-error:
[/B][/B][IMG]https://imgur.com/XiYoCjS[/IMG][IMG]https://i.imgur.com/XiYoCjS.jpg[/IMG][IMG]https://imgur.com/XiYoCjS[/IMG][B][B]

syslog:[/B][/B]
[IMG]https://i.imgur.com/wJncg6N.jpg[/IMG]

Thanks for any help!

---

