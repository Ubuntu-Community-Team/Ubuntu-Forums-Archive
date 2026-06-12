---
title: "Open xdg open? Open xdg open? Open xdg open? Open xdg open?"
date: 2020-10-20
forum: General Help
---

### Post by kytka on 2020-10-20
I like to find out how to get rid of annoying small window asking  repeatedly "Open xdg open? in Chrome browser. Every time this window  comes I must restart Chrome in order to continue browsing. I think  its some kind of malicious virus. Please let me know  what to type it in  terminal to get rid of this nonsense.
Thanks,

---

### Post by CelticWarrior on 2020-10-20
Welcome.

A virus it is not but some malware maybe.

If that's happening it's because the webpage you're visiting is trying to download something.
I would 1) avoid those sites and 2) check the Chrome's extensions for something unfamiliar, something I know I didn't install. And if I were using the same profile in Windows I would check there for virus/malware.

---

### Post by gsahli on 2020-10-20
That add-on is required for ZOOM meetings.

---

### Post by rbmorse on 2020-10-20
Yeah...that would be malware, then.   Ok, it's not, but I HATE zoom meetings.

---

### Post by kytka on 2020-10-21
I found more about "open xdg open?"
[https://www.geeksforgeeks.org/xdg-open-command-in-linux-with-examples/#:~:text=xdg%2Dopen%20command%20in%20the,if%20a%20file%20is%20provided](https://www.geeksforgeeks.org/xdg-open-command-in-linux-with-examples/#:~:text=xdg%2Dopen%20command%20in%20the,if%20a%20file%20is%20provided)
xdg-open command[LEFT] in the Linux system is used to open a file or URL in the user’s preferred application.
The URL will be opened in the user’s preferred web browser if a URL is provided. The file will be opened in the preferred application for files of that type if a file is provided. xdg-open supports [/LEFT]ftp[LEFT], [/LEFT]file[LEFT], [/LEFT]https [LEFT]and [/LEFT]http [LEFT]URLs. This can be used inside a desktop session only. It is not recommended to use xdg-open as root. Here, the zero is an indication of success while non-zero show the failure.
But problem is I don't know what they talking about, please help.
[/LEFT]

---

### Post by dragonfly41 on 2020-10-22
To understand this, search "custom URL protocol handler" to see where this applies.

Also in your gnome-terminal run the command ..

xdg-open "http:www.google.com"
to launch URL in browser.

If a new URL protocol handler is introduced by some vendor, the browser will ask if this is acceptable (from a security perspective).
The URL protocol handler is then registered as "trusted".

In fact I use custom URL protocol handlers for my own development use since they allow hyperlinks in web pages to launch automation scripts. But these scripts can be dangerous if downloaded from an untrusted party.

[https://mattwest.design/registering-protocol-handlers-to-intercept-special-links/](https://mattwest.design/registering-protocol-handlers-to-intercept-special-links/)

[https://en.wikipedia.org/wiki/Uniform_Resource_Identifier#Official_IANA-registered_schemes](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier#Official_IANA-registered_schemes)

[https://askubuntu.com/questions/527166/how-to-set-subl-protocol-handler-with-unity](https://askubuntu.com/questions/527166/how-to-set-subl-protocol-handler-with-unity)

[https://unix.stackexchange.com/questions/497146/create-a-custom-url-protocol-handler](https://unix.stackexchange.com/questions/497146/create-a-custom-url-protocol-handler)

---

### Post by ActionParsnip on 2020-10-22
Just because something you don't understand is happening on your system doesn't mean its a virus

---

### Post by kytka on 2020-10-22
Please, just let me know  what to do get rid of this window: "open xdg open."

---

### Post by CelticWarrior on 2020-10-22
You can't get rid of that unless you remove the underlining cause for the download.

---

### Post by kytka on 2020-10-24
Thank you for your help. :-(

---

