---
title: "clamAV opens instead of associated progarm"
date: 2007-12-08
forum: General Help
---

### Post by Robbyx on 2007-12-08
I use thunderbird as  mail client. When I receive an attachment, sometimes ClamAV opens instead of the associated file. So far there has been no virus reported.  

I would have thought the right thing would be for clamav to hand on the attachment to the associated program but how do I arrange that? 

Anyone know?

Robin

---

### Post by gobbles414 on 2007-12-08
Hi Robbyx,

The problem is with your file associations. This problem of ClamAV trying to open files exists in Firefox too. I have read online that you can set files associations in Thunderbird by going *Tools => Options => Attachments => press the view and edit actions button*. I have not used Thunderbird in long enough, I am not sure if that is correct. But it is worth a try. I know that in Ubuntu itself, you can select file associations by *right-clicking on a file of the type you want to change => properties => open with*.

Personally, I stopped using ClamAV months ago because I could never get the updater to work. I was also never able to get it to correctly interface with Thunderbird. Have you had better luck? I eventually switched to the [free Linux version of Avast!]("http://www.avast.com/eng/download-avast-for-linux-edition.html"). Avast! would not detect test viruses in Thunderbird, but both detects and removes them in Evolution. I do not know if Avast can be set for "real-time" protecting in Ubuntu. I do frequent manual scans of my computer. The free version of AVG for Linux can be configured with a special kernel to do real-time scanning in Linux. But I was not that impressed with AVG's detection abilities even in manual mode.

For security and less bugs, you should always save your attachments to your computer instead of opening them directly in your email client.

---

### Post by Robbyx on 2007-12-08
Hi Robbyx,

The problem is with your file associations. This problem of ClamAV trying to open files exists in Firefox too. I have read online that you can set files associations in Thunderbird by going Tools => Options => Attachments => press the view and edit actions button. I have not used Thunderbird in long enough, I am not sure if that is correct. But it is worth a try. I know that in Ubuntu itself, you can select file associations by right-clicking on a file of the type you want to change => properties => open with.



Personally, I stopped using ClamAV months ago because I could never get the updater to work. I was also never able to get it to correctly interface with Thunderbird. Have you had better luck?

[COLOR="Red"]Yes. I have set up the automatic updater. I did it some months ago and I think I had to add some code into terminal. What is not clear to me is if ClamAV is checking emails attachments as they come in[/COLOR]

 I eventually switched to the free Linux version of Avast!. Avast! would not detect test viruses in Thunderbird, but both detects and removes them in Evolution. 

[COLOR="Red"]What do you think of Evolution? I have really only two complaints about Thunderbird. It is that I can not type in the folder name and find the folder. Also saving messages to folders is a two step operation, once to the defaull folder and saving using one of the message saving addons to the correct folder.
[/COLOR]
I do not know if Avast can be set for "real-time" protecting in Ubuntu. I do frequent manual scans of my computer. The free version of AVG for Linux can be configured with a special kernel to do real-time scanning in Linux. But I was not that impressed with AVG's detection abilities even in manual mode.

For security and less bugs, you should always save your attachments to your computer instead of opening them directly in your email client.

---

### Post by gobbles414 on 2007-12-08
Hi again Robbyx,

**Yes. I have set up the automatic updater. I did it some months ago and I think I had to add some code into terminal. What is not clear to me is if ClamAV is checking emails attachments as they come in.**
I tend to not believe that my email is being scanned unless I see some sort of output. :)


**What do you think of Evolution? ...I cannot type in the folder name and find the folder. Also saving messages to folders is a two step operation...**
Evolution's search does a really great job of finding things -- also very customizable. Saving is easy. In fact, there is even a batch save which can save multiple attachments from within a message to the same directory (literally at the touch of a button). My only complaint is the Evolution insists on sorting contacts by first name if you access you address book from a *new message window*. The address book itself allows all kinds of sorting.

---

### Post by b5baxter on 2007-12-16
I had to use the following steps in order to change the association:
:
1. Install "Mime Edit" from » [https://addons.mozilla.org/en-US/thunderbird/addon/4498 ]("https://addons.mozilla.org/en-US/thunderbird/addon/4498")
3. Go to menu Tools->MIME Edit...
4. Go to Edit tab and click "New Type" button
5. In "MIME type" and "Extension" textfields, type "PDF".
6. Select the radiobutton "Open it with" and choose the path of acroread application by clicking the 'Choose' button.
7. Click OK on all open dialogs and restart Thunderbird.

---

### Post by Robbyx on 2007-12-16
Thanks for that advice. I have adopted it and downloaded the extension. 

Sometimes I find it difficult to find the application on my hard disk. Is there a way to find its location?

Since posting my question about acrobat I have found a good substitute for it:

Kpdf

It is faster on loading and allows for cut and paste. I am very satisfied with it.

R

---

