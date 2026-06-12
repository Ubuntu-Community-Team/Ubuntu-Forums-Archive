---
title: "Problems with Citrix ICA Client"
date: 2005-05-25
forum: General Help
---

### Post by f.prisson on 2005-05-25
Hi everybody,

I just installed the client successfully and it works great. I use my companys secure gateway with firefox. But I have a little problem with it: 

I didn't get the client to be really fullscreen, so that it really seems to be windows. I alway see my Panel and Gnomebar, if I autohide them, there's still a rest to  be seen. So I always have to scroll at the side of the citrix windows. This is being possible for two or three times, then there is no reaction anymore when I scroll. It sometimes works again when I rescale the citrix window. I installed the client about one year ago in a lower verison on a debian and if I remember right I had the same problems.

So I have four questions:

1. Anyone who has noticed this error?
2. Is it possible to make the citrix window really fullscreen, so that the gnome bar is also hidden
3. I use a 1024x768 resolution. Is it possible to start the client with 640x480? In this case there's no need to scroll.
4. Is this behavior defined by the client's resolution or is it pretended by the server? 

Thanks in advance.

---

### Post by sunwave on 2005-07-27
[QUOTE=f.prisson]Hi everybody,

I just installed the client successfully and it works great. I use my companys secure gateway with firefox. But I have a little problem with it: 

I didn't get the client to be really fullscreen, so that it really seems to be windows. I alway see my Panel and Gnomebar, if I autohide them, there's still a rest to  be seen. So I always have to scroll at the side of the citrix windows. This is being possible for two or three times, then there is no reaction anymore when I scroll. It sometimes works again when I rescale the citrix window. I installed the client about one year ago in a lower verison on a debian and if I remember right I had the same problems.

So I have four questions:

1. Anyone who has noticed this error?
2. Is it possible to make the citrix window really fullscreen, so that the gnome bar is also hidden
3. I use a 1024x768 resolution. Is it possible to start the client with 640x480? In this case there's no need to scroll.
4. Is this behavior defined by the client's resolution or is it pretended by the server? 

Thanks in advance.[/QUOTE]
 Hi

I know it's a little bit late for response, but better late than never..

You know that you can inherite Settings from Citrix Terminal Server or NOT.
In your Case you would NOT inherite Settings from the Server and set 'Fullscreen' Modus for your ICA-Client.

Please go and approve the settings:
Start ICA-Client from Menu:
Gnome:
- Applications, Internet, ICA Client
- Select the desired Connection
- Click on Properities-Tab on top
- Select Window
- Activate "Full Screen"

Perhaps you had 'use default' selected or 'percentage of screen size'

Hope it helped..

---

