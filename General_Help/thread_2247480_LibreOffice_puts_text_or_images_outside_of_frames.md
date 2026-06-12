---
title: "LibreOffice puts text or images outside of frames ?"
date: 2014-10-08
forum: General Help
---

### Post by AgentZ86 on 2014-10-08
Ubuntu 14.04 upgraded from 13.04

I insert text or image inside a frame
When you view the document or preview in browser the text is outside the frame as if it's wraping it instead of inserting it into the frame

No wrap feature will change it ?
Is this a known bug ? I use to make documents with text or images in frames all the time either html or writer docs.
It's not hard just insert frame, then click in the frame and type something

Now what ? 

Please advise 
Thanks

---

### Post by mcparty2 on 2014-10-08
I have just tried this, and the same behaviour happens to me in LibreOffice Version 4.2.6.3 Build ID: 420m0(Build3) Are you using the same version?

Open LibreOffice > Select Writer > insert Frame > type in contents > click File > preview in browser.

I tried saving as html then and the same behaviour occurs. Unfortunately I am not sure if this is expected behaviour or not.
I have not used LibreOffice to produce webpages, it would probably be worth while learning some CSS/HTML in order to achieve the results you are looking for then using your preferred test editor to generate the code you require.

Eitherway, to be more helpful, I shall have a play around to see if i can find a way around it. 

Thanks

---

### Post by mcparty2 on 2014-10-08
I cannot get it to work i'm afraid. Looking at the HTML that it generates it not putting the text in the box - Most probably a bug. 

If you are looking for a GUI for creating HTML pages have a look at KompoZer. You should find it in the Ubuntu repositories. [http://www.kompozer.net/](http://www.kompozer.net/)

Also, here is some HTML code for a simple text box if you wanted to go down the route of writing html from a text editor:

```
<p><input maxlength="128" name="box1" type="text" value="Text in the box" /></p>
```

I hope this helps :)

---

### Post by AgentZ86 on 2014-10-10
Thanks
I thought perhaps a bug too

I use to use Kompozer all the time and loved it but don't see it in the repose anymore 

I'll try to install thanks

---

