---
title: "No image thumbnail previews in Thunar or Nautilus / Nautilus as default File Manager"
date: 2013-09-18
forum: General Help
---

### Post by RallyDarkstrike on 2013-09-18
Hi guys,

I know Thunar comes with Xubuntu 12.04 by default, and it works ok, but there are a few things I don't like about it (such as the fact it can only be set to one view mode ever, whereas Nautilus can remember view modes for specific folders). I use Nautilus as my primary File Manager on my Linux Mint 14 netbook and I love it. Mint 14 came with Thunar as default too, but changing it to Nautius was as easy as pie in the system settings.

However, in Xubuntu, even if I set Nautilus as the default under the "Settings Menu" in "Preferred Applications, Thunar is still the File Manager that runs when I double-click on Home on my desktop....how do I permanently set Nautilus as my default...?

NOW...my second issue....image thumbnail previews aren't working in either Nautilus OR Thunar. If I view a folder with images, all I see is that generic "image" icon for everything...any thoughts on why this is or how to fix it? I DO have both Thunar and Nautilus set to show thumbnails. I was told I need Tumbler installed, and, as far as I can tell, it is. I was also told I could try deleting my .thumbnails folder....thumbnails still aren't working. Finally (at least for Thunar), I was told I could try deleting my Thunar configuration...this also didn't solve the problem.

Any help would be greatly appreciated! :)

---

### Post by paulsantman on 2013-10-14
Hi RallyDarkstrike,

I had exactly the same problem with Xubuntu 13.04. I googled a bit and eventually started digging myself in various folders.

And I found out that ~/.thumbnails was owned by Root! So then I only saw thumbnails in Thunar when I was running Thunar as root.

Changing the permissions of this folder fixed the problem for me. 

And do not forget to install the package tumbler, which Thunar uses to generate thumbnails.

---

### Post by RallyDarkstrike on 2013-10-15
> **paulsantman said:**
> Hi RallyDarkstrike,

I had exactly the same problem with Xubuntu 13.04. I googled a bit and eventually started digging myself in various folders.

And I found out that ~/.thumbnails was owned by Root! So then I only saw thumbnails in Thunar when I was running Thunar as root.

Changing the permissions of this folder fixed the problem for me. 

And do not forget to install the package tumbler, which Thunar uses to generate thumbnails.

Hi!

Thanks for the reply - I never thought to check that, I'll have to give it a go and see if that works for me! I DO know I have Tumbler installed already, as I had checked that while trying to find out why the thumbnails weren't working...

---

### Post by melchordioso58 on 2013-11-18
> **paulsantman said:**
> Hi RallyDarkstrike,

I had exactly the same problem with Xubuntu 13.04. I googled a bit and eventually started digging myself in various folders.

And I found out that ~/.thumbnails was owned by Root! So then I only saw thumbnails in Thunar when I was running Thunar as root.

Changing the permissions of this folder fixed the problem for me. 

And do not forget to install the package tumbler, which Thunar uses to generate thumbnails.

thank you! ive been looking for this. :)

---

