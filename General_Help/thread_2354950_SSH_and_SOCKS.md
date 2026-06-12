---
title: "SSH and SOCKS"
date: 2017-03-07
forum: General Help
---

### Post by bladez99 on 2017-03-07
[h=2][/h][COLOR=#000000][INDENT]Can someone explain to me what is happen with this command. I know it is a reverse ssh. But can someone explain in detail since there is a sock proxy and reverse ssh and how that works. 

ssh -o ProxyCommand=' nc -x 1.1.1.1:1080 %h %p' -o StrictHostKeyChecking=no -f -i /var/lib/dir/dir/data/key -R 1477:localhost:9050 -p 80 [EMAIL="zuulsupport@t2.candiworks.com"]username@url.com[/EMAIL] sleep 7200

Do note that 1477 keeps changing dynamically. 

Can someone explain to me, how this is suppose to work? Or what happens in a process / flow view.[/INDENT]
[/COLOR]

---

