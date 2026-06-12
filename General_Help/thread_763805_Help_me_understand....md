---
title: "Help me understand..."
date: 2008-04-23
forum: General Help
---

### Post by therapture on 2008-04-23
OK, so I tossed up an idea on Brainstorm (link at the end of this post) and I can't understand why this would not be a good idea. Maybe it's because I have a programming background and I only see the good that could come of it. I'll give you the quick run down, and if you think this is a bad idea please help me understand why it is such.

It boils down to this: Many many many sites out there allow you to upload a file from your computer to a site. Many of those sites also limit what types of files you can upload (for obvious security reasons) and they limit them based on their file extension. Because of the case sensitive nature of linux, these extensions are taken literally when they are not meant to be so. For example, Flickr allows you to upload *.jpg files, but they do not mean that literally. You should also be able to upload *.JPG, *.Jpg, *.jpG and whatever other case combinations may be in the extension. 

The problem is, because it is interpreted literally, the app will not even list somefile.JPG in your upload dialog box because the case is different than what was programmed into the app (lowercase jpg). A bigger problem is that most cameras today create files with capital extensions such as DSC0001.JPG. This causes a person to manually rename files, and if it's more than one then it becomes an unpleasant task. And that's only if someone new to linux even figures out why their files aren't showing up in the first place. 

This has caused sites like Flickr (again, just a single example. There are tons of sites crippled by this) to have to rewrite their apps to include *.jpg, *.JPG, *.jpeg, *.JPEG and so on. A link in the brainstorm post shows how this caused the dialog box to grow to an enormous width.  

So my proposal was that, when the dialog box looks for the predefined extensions you are allowed to upload, it should search for the extensions (and only the extensions) without paying attention to case. This way, a user will still be able to choose somefile.jpg and someotherfile.JPG as the site truly wanted. 

One commenter, who I agree with, suggested that people are voting the idea down because they don't understand it. There was a comment about "Linux should not be case insensitive", and the example I used there was with the myspace photo upload app so maybe people thought this was a myspace problem, who knows. I guess I didn't choose my words carefully when making the subject line and thought people were actually going to read the content before voting.

The idea is here, and it currently sits at -8: [http://brainstorm.ubuntu.com/idea/7388/](http://brainstorm.ubuntu.com/idea/7388/)

Please cast your thoughts, but I ask that you at least understand what I proposed before commenting. Try this with sites like myspace or somewhere else you can upload files, but note that this does not happen where the file upload dialog file type is "All files". These webapps weed out bad files in the app itself. Sites like myspace and flickr, however, give you a restricted prompt and define the file type beforehand, and THAT'S the issue here.  Thanks.

---

### Post by blazemore on 2009-02-02
And how is this a problem with Ubuntu...?
It sounds like a problem with Myspace, and your digital camera

---

### Post by mb_webguy on 2009-02-02
Agreed.  This is simply bad programming on the part of those specific web sites.  Users shouldn't have to cater to web sites;  web sites should cater to their users.  The best solution should be to contact MySpace (and the other web sites you use that have this problem) and inform them of the issue.  It should be a simple fix -- all they have to do is use regular expressions instead of hard-coded file extensions, and automatically change the case of file extensions when they are uploaded, which can probably be done with a single simple command depending on the scripting language being used.

In the meanwhile, it's fairly easy to convert the extension of all files of a given type to lowercase, either using a script or an application.  I believe KRename has this feature.

---

