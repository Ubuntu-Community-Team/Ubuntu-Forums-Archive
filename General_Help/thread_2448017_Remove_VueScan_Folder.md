---
title: "Remove VueScan Folder"
date: 2020-07-30
forum: General Help
---

### Post by daniell59 on 2020-07-30
I would like to remove the VueScan folder.

Ubuntu 20.04 64

Thanks

---

### Post by ajgreeny on 2020-07-30
Tell us more.

What VueScan folder are you talking about?
Have you installed VueScan, and then subsequently uninstalled it?
We can do nothing to help without more information, so help us to help you.

---

### Post by daniell59 on 2020-07-30
I am new to Ubuntu 20.04. Please forgive my ignorance. When I hit applications, I see a folder that I would like to remove.

Thanks

---

### Post by ajgreeny on 2020-07-30
I see now from your previous threads that you have installed VueScan in the past and now presumably want it totally removed.

However, most of us probably have no idea what folders or files the vuescan.deb archive installs into the system; I certainly don't, so as I said above tell us in more detail what you want and I'm sure we can tell you what to do.

---

### Post by daniell59 on 2020-07-30
> **ajgreeny said:**
> I see now from your previous threads that you have installed VueScan in the past and now presumably want it totally removed.

However, most of us probably have no idea what folders or files the vuescan.deb archive installs into the system; I certainly don't, so as I said above tell us in more detail what you want and I'm sure we can tell you what to do.

You summed it up  perfectly well. I don't know what more to say.

---

### Post by daniell59 on 2020-07-30
This is all I can find on their site.

On Linux, delete these two files: ~/.vuescanrc /etc/.vuescanrc (if it exists)

---

### Post by grahammechanical on 2020-07-30
If we install an application from the command line it should present itself in Ubuntu Software/app store. From there we should be able to remove the application. Based upon the purpose of Vuescan it should put a data folder in the users home folder. These folders do not get removed when we remove/uninstall an application. 

To remove these kinds of data folders we use the file manager (files). It has the icon of a filing cabinet drawer. The file manager will open in your home folder. Find the folder from Vuescan. Select it. Right click on it to bring up a menu and select "Move to rubbish bin."

From the Ubuntu Desktop Guide (help)

> [COLOR=#3C3C3C][FONT=sans-serif]If you do not want a file or folder any more, you can delete it. When you delete an item it is moved to the [COLOR=#6C6C6C]Trash[/COLOR] folder, where it is stored until you empty the trash. You can [restore items]("xref:files-recover") in the [COLOR=#6C6C6C]Trash[/COLOR] folder to their original location if you decide you need them, or if they were accidentally deleted.[/FONT][/COLOR][COLOR=#3C3C3C][FONT=sans-serif][COLOR=#6C6C6C]**[B]To send a file to the trash:**

[/B][/COLOR]

[LIST]
[*]Select the item you want to place in the trash by clicking it once. 
[*]Press Delete on your keyboard. Alternatively, drag the item to the [COLOR=#6C6C6C]Trash[/COLOR] in the sidebar. 
[/LIST]


[/FONT][/COLOR]
[COLOR=#3C3C3C][FONT=sans-serif]The file will be moved to the trash, and you&#8217;ll be presented with an option to [COLOR=#6C6C6C]Undo[/COLOR] the deletion. The [COLOR=#6C6C6C]Undo[/COLOR] button will appear for a few seconds. If you select [COLOR=#6C6C6C]Undo[/COLOR], the file will be restored to its original location.[/FONT][/COLOR][COLOR=#3C3C3C][FONT=sans-serif]To delete files permanently, and free up disk space on your computer, you need to empty the trash. To empty the trash, right-click [COLOR=#6C6C6C]Trash[/COLOR] in the sidebar and select [COLOR=#6C6C6C]Empty Trash[/COLOR].
[/FONT][/COLOR]

If I have guessed right, do I get a biscuit? I am English. So, I do not eat cookies unless they are chocolate chip. :)

Regards.

P.S. A folder must be emptied before we can move it to the rubbish bin/delete it.

---

### Post by daniell59 on 2020-07-30
> **grahammechanical said:**
> If we install an application from the command line it should present itself in Ubuntu Software/app store. From there we should be able to remove the application. Based upon the purpose of Vuescan it should put a data folder in the users home folder. These folders do not get removed when we remove/uninstall an application. 

To remove these kinds of data folders we use the file manager (files). It has the icon of a filing cabinet drawer. The file manager will open in your home folder. Find the folder from Vuescan. Select it. Right click on it to bring up a menu and select "Move to rubbish bin."

From the Ubuntu Desktop Guide (help)



If I have guessed right, do I get a biscuit? I am English. So, I do not eat cookies unless they are chocolate chip. :)

Regards.

P.S. A folder must be emptied before we can move it to the rubbish bin/delete it.

I wish that I could say good show mate

When I press it once, it opens up.

---

### Post by daniell59 on 2020-07-31
It was so obvious that I forgot about how to remove it. I went to installed programs and removed it.

---

