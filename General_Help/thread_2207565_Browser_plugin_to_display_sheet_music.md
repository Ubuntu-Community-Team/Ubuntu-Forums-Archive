---
title: "Browser plugin to display sheet music?"
date: 2014-02-24
forum: General Help
---

### Post by rdh61 on 2014-02-24
Hi,

Can anybody please tell me which browser plugin is required to correctly display the sheet music on these pages?

[http://www.easymusicnotes.com/index.php?option=com_content&view=article&id=909:jamaica-farewell&catid=146:piano-level-2&Itemid=155](http://www.easymusicnotes.com/index.php?option=com_content&view=article&id=909:jamaica-farewell&catid=146:piano-level-2&Itemid=155) (the PDF music score after the video)

[http://www.musicnotes.com/unsupported.asp?BadBrsr=true&ppn=MN0076787](http://www.musicnotes.com/unsupported.asp?BadBrsr=true&ppn=MN0076787)  (the whole page)

Thank you.

---

### Post by ajgreeny on 2014-02-24
Easymusicnotes, your first link shows me the PDF in Firefox without any added plugin, but having set FF preferences to preview the document in FF, as per my screenshot, which shows the preview also shown in screenshot 2.

The second link will not work as it detects a Linux OS is being used, and even trying the FF User-agent-switcher add-on to emulate a Windows OS was not successful.

---

### Post by rdh61 on 2014-02-24
Thanks ajgreeny, that worked. By any chance, have you any idea how to do the same in chromium? I just see a grey area with a jigsaw puzzle icon and the text "No plug-in available to display this content." I can't find a similar setting to the one in FF.

---

### Post by Xanthius on 2014-02-24
I got to be honost with you, I've not noticed this issue before this topic. But the problem is simple as there is no PDF viewer installed by default (atleast for me).
You can check this out by going into your settings by using this "chrome://plugins/" without the quotes as URL.

If its not listed:
1. Download your package of chrome here: [https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)
2. Open that .deb file with your archive manager.
3. Extract "opt/google/chrome/libpdf.so"
4. Open your terminal.
5. "cd to/your/extracted/directory"
6. sudo mv libpdf.so /usr/lib/chromium-browser
7. Restart your browser and it should work.

I'm sure there are faster ways to move that file directly from the archive to the right directory, but I'm not that experienced..
But this is atleast safe, I would not want you to move your download directory to your plugins directory of Chrome.
You could also use cp instead of mv, but it be a waste of space.


And while at it, you might want to use a different Adobe Flash player as well. The build in one doesn't really work with addblocker anymore incase you use it.
Not only that, it isn't being updated anymore and chrome is switching over to the new "Pepper API" (PPAPI).

---

### Post by ajgreeny on 2014-02-24
Sorry, I can't help with chromium as I seldom use it, mainly because it does not have some of the plugins that I use all the time in FF, paticularly Tab-Mix-Plus, which is the one I can't manage without, and this pdf preview.

---

