---
title: "Firefox very slow trough VNC connection"
date: 2021-10-30
forum: General Help
---

### Post by marcodea on 2021-10-30
[COLOR=#232629][FONT=-apple-system]I'm using a minipc (8GG ram, 128GB sd, Intel Celeron J4125I) with Xubuntu 20.04.3 LTS. It runs well but with good performance. I'm installed vino to access the server remotely with a VNC client (windows) and the performance is good. My only issue comes using Firefox and other web browsers. Any browser is very slow and it's not possible to use. Other apps, ie Liberoffice Calc, video player etc. work fine trough VNC.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]
[IMG]https://drive.google.com/file/d/112o7CUNsPHf-n9HymOCjXTh7ymaNugPa/view?usp=sharing [/IMG][IMG]https://drive.google.com/file/d/1Vcii2WcSGrAj8OkX48BRCriHU04-c-I8/view?usp=sharing [/IMG][IMG]https://drive.google.com/file/d/1DvGQfO18cO4P4M8tyl46PhdrU3JBFnWi[/IMG]Any suggestion? Kind regards[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]
[/FONT][/COLOR]

---

### Post by HermanAB on 2021-10-30
Yes.  Don’t use VNC.  Learn to use SSH instead.

---

### Post by bunny9000 on 2021-10-30
X2go has you covered to access your server as it uses SSH. You'll need to install the server on the server and the client on the windows machine and you'll get a faster, more secure experience than VNC.

VNC has a bunch of security flaws I wouldn't ever access a server using it.

---

### Post by HermanAB on 2021-10-31
Btw Windows nowadays has SSH available.

---

### Post by ActionParsnip on 2021-10-31
What are you doing on the remote system that needs the full desktop session? Why are you connecting to the remote system using VNC? There may be a sleeker solution to what you want to achieve...

---

### Post by ActionParsnip on 2021-10-31
Why run a Web browser on a remote system using VNC when you have a local browser (surely)... Seems like a weird use case.

---

### Post by marcodea on 2021-11-03
Thanks for your advice. I'll investigate SSH.

@ActionParsnip: I prefer using the browser on remote server, instead of my computer, for security reason.

Have a great day.

---

### Post by ActionParsnip on 2021-11-03
> **marcodea said:**
> Thanks for your advice. I'll investigate SSH.

@ActionParsnip: I prefer using the browser on remote server, instead of my computer, for security reason.

Have a great day.

Then setup an SSH tunnel and you can proxy the traffic through the remote system rather than running the browser on the remote system. The traffic will appear to come out of the remote system rather than your local PC. Are you trying to change the perceived location of your traffic? Is this the goal?

---

