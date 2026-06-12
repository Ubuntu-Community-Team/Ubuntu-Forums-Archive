---
title: "can you tell thunderbird not to load images of feeds?"
date: 2022-05-18
forum: General Help
---

### Post by ronjjjg8885 on 2022-05-18
i'm using the program for rss feeds. but the feeds items are loaded with the images when images are available.

how to disable images and have more privacy by that?

---

### Post by #&amp;thj^% on 2022-05-18
This can be tricky  for different versions so here is a few suggestions to try:

[list]
In Thunderbird, 
[*]go to Tools -> Options -> Select 'Privacy' Tab

[*]Deselect 'Allow Remote Content in Messages'

If this doesn't work try; 
[*]Go to Tools -> Options -> Select 'Advanced' Tab Go to General Tab Open Config Editor. Change switch of [/list]
```
mailnews.message_display.disable_remote_image to FALSE
```
If one works for you>>will you post which one worked?

---

### Post by ronjjjg8885 on 2022-05-19
in 'tools' there is no 'option' option..

perhaps they have changed that?

---

### Post by #&amp;thj^% on 2022-05-19
> **ronjjjg8885 said:**
> in 'tools' there is no 'option' option..

perhaps they have changed that?

Sorry I had a very busy day yesterday: Tools should have been worded** Preferences>>Privacy & Security see screenshot.**
Or go to Preferences>>General and at the bottom hit the Config Editor and search for in the **URL bar  in the Advanced Tab** "mailnews.message_display.disable_remote_image"
And change that to "FALSE"
Hope this is clear enough. :)

---

### Post by ronjjjg8885 on 2022-05-20
thank you very much.
i did both steps but still see images.
maybe they are attachments or something??

---

### Post by #&amp;thj^% on 2022-05-20
I would have to see one first to tell. (Not necessary though)
 The image/s would have been stored in the TB cache, but not permanently in the mbox file, in accordance with the Sync. & Storage settings.  So, I would say that TB does download embedded images and attachments by default, but in this case only after you choose to open the message, and then the content i**s only cached on the local computer.**

You can exclude/include specific sites from the rule. Click the** Exceptions**&#8230; button, type the website or email address and click **Block **or **Allow.** 
Source to help: [https://support.mozilla.org/en-US/kb/remote-content-in-messages](https://support.mozilla.org/en-US/kb/remote-content-in-messages)

---

### Post by ronjjjg8885 on 2022-05-22
ill try that later thanks

---

### Post by walts48 on 2022-05-23
> **ronjjjg8885 said:**
> i'm using the program for rss feeds. but the feeds items are loaded with the images when images are available.

how to disable images and have more privacy by that?

For Blogs & News Feeds try View > Feed Message Body As > Summary.

---

### Post by ronjjjg8885 on 2022-05-24
it's already on summry
i've switched to text only mode

---

### Post by mIk3_08 on 2022-05-26
> **1fallen said:**
> Sorry I had a very busy day yesterday: Tools should have been worded** Preferences>>Privacy & Security see screenshot.**
Or go to Preferences>>General and at the bottom hit the Config Editor and search for in the **URL bar  in the Advanced Tab** "mailnews.message_display.disable_remote_image"
And change that to "FALSE"
Hope this is clear enough. :) 
This works for me. [screenshot] When I unchecked the radio box all email with images won't display/load the images. But when I checked the radio box. Whenever I open email with images. It loads all the images completely. Thanks for sharing. Regards and Cheers.

---

### Post by ronjjjg8885 on 2022-06-03
i think it is still not solved because some feeds do show images.

i can't switch to an rss syndication program because i need the RTL features on thunderbird..

---

