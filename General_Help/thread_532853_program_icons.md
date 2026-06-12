---
title: "program icons"
date: 2007-08-23
forum: General Help
---

### Post by BDNiner on 2007-08-23
Where can i find all the program icons? The icons that are displayed in the applications menu. I would like the icons for applications open in AWN to be the same as the ones from the Applications menu.

---

### Post by gashcrumb on 2007-08-23
They're all under /usr/share/icons and then under whatever icon theme name you're using, in there either "scalable/apps" or "24x24/apps".  So for the default "Tangerine" icon theme:

/usr/share/icons/Tangerine/scalable/apps

or

/usr/share/icons/Tangerine/24x24/apps

---

### Post by BDNiner on 2007-08-23
That is not what i was looking for, let me explain better (i hope). I have good earth installed, when i run it the icon on my AWN bar is different from the one in my Applications menu. When can i find the icons in the applications menu so that i can manually load them into the AWN bar?

---

### Post by mcduck on 2007-08-23
> **BDNiner said:**
> That is not what i was looking for, let me explain better (i hope). I have good earth installed, when i run it the icon on my AWN bar is different from the one in my Applications menu. When can i find the icons in the applications menu so that i can manually load them into the AWN bar?
Like gashcrumb said, they are in /usr/share/icons, under the theme you are currently using. You may also find soma application icons in /usr/share/pixmaps. And if your current theme doesn't have icon for the app your best bet is to check under Tango theme.

If you want to check the exact icon a certain app in your menu is currently using, right-click on the menu, select "Edit Menus", find your app, right-click it, select "Properties", click the icon image and copy the path from the browser window that opens.

I hope this answered your question.

---

### Post by BDNiner on 2007-08-23
Thank you mc duck. That was the answer i needed. I am still trying to wrap my head around how the file system works. I have figured out that "/home" plays almost the same role as "Documents and Settings" from windows. I just need to figure out where "Program Files" and "%System" are and i think i will be fine.

---

### Post by mcduck on 2007-08-25
> **BDNiner said:**
> Thank you mc duck. That was the answer i needed. I am still trying to wrap my head around how the file system works. I have figured out that "/home" plays almost the same role as "Documents and Settings" from windows. I just need to figure out where "Program Files" and "%System" are and i think i will be fine.

There isn't exact "Program Files", as all files are divided based on what they are used for instead of what program they belong to. But it helps to know that almost always you'll find the executable file from /usr/bin, documents from /usr/share/doc and rest of important stuff from /usr/share/programname. Pretty much all system settings are in /etc.

This might help you: [http://articles.techrepublic.com.com/5100-6345-5031957.html]("http://articles.techrepublic.com.com/5100-6345-5031957.html")

---

