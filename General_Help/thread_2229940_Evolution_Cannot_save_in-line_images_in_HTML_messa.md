---
title: "Evolution: Cannot save in-line images in HTML message"
date: 2014-06-16
forum: General Help
---

### Post by craig10 on 2014-06-16
Hi there,

I have Evolution 3.8.4, which seems to be the latest version available from the Ubuntu Software Centre. According to the Evolution documentation installed with the application:

"To save an image that is embedded in an HTML email, right-click on the image and click Save Image...."

However, I have no such option in my right-click menu. In fact, the right-click menu remains exactly the same whether I right-click on an image or on the text of the message.

The image I am trying to save is a local image -- i.e., it was downloaded with the message. It was sent with iPhone Mail, but the sending client should affect Evolution's behaviour.

Things I have tried that have not worked:

[LIST]
[*]Saving the message as an "mbox" file and opening it with Thunderbird. This just results in a new message with the "mbox" file attached. 
[*]Dragging the image to the desktop. This results in a file named "Link to cid:F59DD7B9-B1C9-48F4-A63A-34696CC5E7C5". Double-clicking that opens Gedit, with the error message, "Could not open the file cid:///F59DD7B9-B1C9-48F4-A63A-34696CC5E7C5. gedit cannot handle cid: locations." 
[*]Dragging the image to the desktop while holding the shift of ctrl keys results in an error dialogue box that reads: "Error while copying. There was an error getting information about “F59DD7B9-B1C9-48F4-A63A-34696CC5E7C5”. The specified location is not supported". The options are Cancel, Skip All, Skip or Retry. Retry results in the same error. 
[*]Viewing the source of the message only shows the MIME encoding. I was hoping it would show me the path to where the images are stored on the hard drive. 
[*]Message | Edit as New Message results in a message with a .dat attachment that isn't the image, and couldn't possibly be as it's only a few kilobytes in size while the image is several megabytes. 
[/LIST]

The contents of the "Link to cid:F59DD7B9-B1C9-48F4-A63A-34696CC5E7C5" file on the desktop in the second thing I tried above are:

```
[Desktop Entry]
Encoding=UTF-8
Name=Link to cid:F59DD7B9-B1C9-48F4-A63A-34696CC5E7C5
Type=Link
URL=cid:F59DD7B9-B1C9-48F4-A63A-34696CC5E7C5
Icon=text-html
```

However, this is not helpful.

 Anybody have any ideas as to how I can extract and save this image, or perhaps upgrade Evolution to the latest version (3.12.2) to see if that will help?

Thanks.


Craig

---

### Post by craig10 on 2014-06-18
Does nobody use Evolution?

---

### Post by craig10 on 2014-06-18
Further to this, the behaviour above only seems to happen with messages where the image is embedded and accompanies the email -- i.e., the image is local. With emails where the embedded image is remote -- i.e., it's on a web server -- I get the "Save image" right-click menu option, but it doesn't do anything. Same with the "Copy image" option.

---

