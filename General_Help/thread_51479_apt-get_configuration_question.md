---
title: "apt-get configuration question"
date: 2005-07-24
forum: General Help
---

### Post by vkkim on 2005-07-24
Hi, I had tor, privoxy, and anon-proxy previously installed but uninstalled them recently.  Afterwards, apt-get continued to try and connect to proxy servers on localhost but since they're not there anymore apt-get just gives me connection errors.  How can I tell it to make a direct connection without the proxy again?  Also, lynx and w3m do not work either.  Thanks.

[Actually, the reason I uninstalled them was because I couldn't get them to work in the first place... so if someone could point me to a guide to installing tor and getting it to work in Hoary that would be good too.  But I still want to know how to configure apt...]

---

### Post by PeP on 2005-07-24
[QUOTE=vkkim]Hi, I had tor, privoxy, and anon-proxy previously installed but uninstalled them recently.  Afterwards, apt-get continued to try and connect to proxy servers on localhost but since they're not there anymore apt-get just gives me connection errors.  How can I tell it to make a direct connection without the proxy again?  Also, lynx and w3m do not work either.  Thanks.

[Actually, the reason I uninstalled them was because I couldn't get them to work in the first place... so if someone could point me to a guide to installing tor and getting it to work in Hoary that would be good too.  But I still want to know how to configure apt...][/QUOTE]
 you might have told apt that you have a proxy, then try
% grep -rin proxy /etc/apt
if you have a positive match,comment it


else you have told your shell that you have a proxy 
try:
% echo $http_proxy
then look (I mean grep -rin theb comment any match) 
in your  ~/.bashrc and in /etc/bashrc if you have bash,
in ~/.zshrc and /etc/zsh/ if you use zsh.

---

### Post by vkkim on 2005-07-25
[QUOTE=PeP]you might have told apt that you have a proxy, then try
% grep -rin proxy /etc/apt
if you have a positive match,comment it


else you have told your shell that you have a proxy 
try:
% echo $http_proxy
then look (I mean grep -rin theb comment any match) 
in your  ~/.bashrc and in /etc/bashrc if you have bash,
in ~/.zshrc and /etc/zsh/ if you use zsh.[/QUOTE]

I tried both and got

"bash: fg: %: no such job"

both times...

---

### Post by PeP on 2005-07-27
[QUOTE=vkkim]I tried both and got

"bash: fg: %: no such job"

both times...[/QUOTE]

The '%' (precent symbol) means you should type the following characters in a terminal. It is a common convention, just as the '#' symbol means you should type something in as root.

So if you read 
% foobar

Just type in:
foobar
without the percent indicating it is a command you have to type in.

---

### Post by vkkim on 2005-07-28
[QUOTE=PeP]The '%' (precent symbol) means you should type the following characters in a terminal. It is a common convention, just as the '#' symbol means you should type something in as root.

So if you read 
% foobar

Just type in:
foobar
without the percent indicating it is a command you have to type in.[/QUOTE]

Thanks a lot! Now I feel stupid... 

Anyway when I type in echo $http_proxy, I get

[http://localhost:4001](http://localhost:4001)

which is where my proxy used to be.  How do I change that?  Also, I still don't quite understand your directions after echo...

---

### Post by PeP on 2005-08-08
[QUOTE=vkkim]Thanks a lot! Now I feel stupid... 

Anyway when I type in echo $http_proxy, I get

[http://localhost:4001](http://localhost:4001)

which is where my proxy used to be.  How do I change that?  Also, I still don't quite understand your directions after echo...[/QUOTE]
grep -rin gives you the name of a file and a line where there is a match.

for exemple if you /etc/bashrc 

to change the value open the file 
%sudo gedit /etc/bashrc 
and modify the corresponding line 
(replace gedit by kedit if you use kde)

If you do not want anymore proxy, just comment the line, it ios done by adding a special character (often '#' ) at the beginning of the line.

Then you have to 'restart' the application that uses this config file

you might also want to overwrite the $http_proxy value 'on the run' without changing the defaults settings, then just type

%export http_proxy='myproxy:port'

(no $ at the beginning when you want to write it)
or to desactivate the proxy setting:

%export http_proxy=''

be also aware that there might be a $ftp_proxy and a $hftp_proxy set.

usually, you find the same commands in your shell conf file (/etc/bashrc, /etc(/zsh)/zshenv ... depending on what you use) so if you want to change the value permanently add the command there.

good luck,

---

