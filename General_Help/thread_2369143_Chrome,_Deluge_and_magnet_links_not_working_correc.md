---
title: "Chrome, Deluge and magnet links not working correctly"
date: 2017-08-19
forum: General Help
---

### Post by Paddy Landau on 2017-08-19
When I select a magnet link, Chrome uses xdg-open (see attached screenshot), which then opens Deluge.

Unfortunately, Deluge doesn't register the magnet link. I have to add it manually.

I have scoured various forums, and quite possibly got myself confused, but I haven't found the answer.

Using the Lubuntu download as an example, the following works from the command line (it opens Deluge with a prompt to add the magnet):
```
deluge-gtk 'magnet:?xt=urn:btih:c1aa77dea674d71fbd85559034b6082b8434d36e&dn=lubuntu-16.04.3-desktop-amd64.iso'
```
But the following doesn't work (it just opens a new Chrome browser window):
```
xdg-open 'magnet:?xt=urn:btih:c1aa77dea674d71fbd85559034b6082b8434d36e&dn=lubuntu-16.04.3-desktop-amd64.iso'
```
To clarify: What happens now is that when I click a magnet link in Chrome, it just opens Deluge. What I want to happen is that when I click a magnet link in Chrome, it opens Deluge with a prompt to add the magnet (exactly as if I had entered the deluge-gtk command above).

How can I get this to work, please?

I'm using Lubuntu 16.04 64-bit.

---

### Post by SeijiSensei on 2017-08-19
Transmission handles magnet links correctly for me.  I use Firefox, not Chrome, though.

---

### Post by Paddy Landau on 2017-08-19
Thanks, SeijiSensei, but that doesn't answer my question at all. I use Chrome and Deluge.

---

### Post by SeijiSensei on 2017-08-20
I'm generally pretty agnostic about software.  There are so many options, if something doesn't work, I try a different program.

That said, clicking on magnet links in Chrome also launched Transmission for me.

---

### Post by sp40140 on 2017-08-20
I use FireFox as well. 
But just tried with Chrome as well and it works fine for me. 
When I am at the screen which you posted above, I just click open and it opens deluge and starts downloading the lubuntu.
I can't think of any specific settings I tweaked or not. 
But if you want me to check something, let me know.

---

### Post by Paddy Landau on 2017-08-20
> **SeijiSensei said:**
> I'm generally pretty agnostic about software.  There are so many options, if something doesn't work, I try a different program.
That's fine, but it's pretty inconvenient to open another browser, copy the URL across, and click the magnet link. It's much faster to just copy the download link and manually add it to Deluge.

> **sp40140 said:**
> But just tried with Chrome as well and it works fine for me.
Thanks. I can't imagine what setting it might be; I have Googled and tried every setting that has been recommended, from xdg-mine and gvfs-mime to "Associate Magnet links with Deluge". I can only get Deluge to open but not to automatically download.

Are you using Ubuntu? I wonder if that makes a difference, as I'm using Lubuntu.

---

### Post by Paddy Landau on 2017-08-20
Ah, I found it!

It was a typo in the deluge-gtk.desktop.

Pfft, my fault!

It's all fixed.

Thanks for your time!

---

### Post by LowSky on 2017-11-16
> **Paddy Landau said:**
> Ah, I found it!

It was a typo in the deluge-gtk.desktop.

Pfft, my fault!

It's all fixed.

Thanks for your time!

How did you fix the issue? I can't get Chrome to open magnet links. It works fine in Firefox.

---

### Post by Paddy Landau on 2017-11-17
> **LowSky said:**
> How did you fix the issue? I can't get Chrome to open magnet links. It works fine in Firefox.
Sorry, I don't remember now!

Indeed, I seem to no longer have [FONT=lucida console]deluge-gtk.desktop[/FONT], only [FONT=lucida console]deluge.desktop[/FONT].

I've attached my [FONT=lucida console]deluge.desktop[/FONT] file, which you can compare to yours to find if there is any difference.

---

