---
title: "The firefox file picker and unity file manager"
date: 2014-12-16
forum: General Help
---

### Post by D_J on 2014-12-16
I am using Ubuntu 14.04 and I'm having troubles dealing with the Firefox file picker. I'm not sure if this is the right place to post this but I'll start from the beginning.

I do not like unity's file manager nautilus what so ever. It's missing 4 features which seems ridiculous to be missing.
 
[LIST=1]
[*]If you open another hard drive     with nautilus and try to click the icon on the task-bar to get the     window back in focus, it just opens a new instance. 
[*]You cannot open a terminal at the     currently browsed directory. 
[*]The view modes: icons and list     cannot be remembered for what directory that you set it to. So if I     set the view to icons for my pictures directory, then it will apply     globally to other directories like $HOME. 
[*]The zoom level cannot be remember for what directory that you     set it to. So if I set the zoom level to whatever zoom for my     pictures directory, then it will apply globally to other directories     like $HOME. 
[/LIST]
 
Due to this, I tried switching to a different file manager with the features I wanted which is nemo. I managed to set the default file manager to it by [https://sites.google.com/site/installationubuntu/tweaking-ubuntu/change-default-filemanager](https://sites.google.com/site/installationubuntu/tweaking-ubuntu/change-default-filemanager).

But the problem is that Firefox didn't change its file picker, I believe it's still using unity/nautilus?
This is a no go for me because
 
[LIST=1]
[*]I cannot even view the directory     as thumbnails/icons. 
[*]I cannot even zoom. 
[/LIST]
 This seems ridiculous for when I want to upload pictures. I would basically have to open nemo in the background, find the image there then type in the filename in the cruddy firefox file picker. I can't stand for such a convoluted process just to upload pictures. And along with that, if I open the containing folder option in downloads, it opens up nautilus instead!

 So I tried doing some trial and error for changing the file picker. I tried going into Firefox's config page (about:config) and searching ui.allow_platform_file_picker and setting it to false. The new dialogue looks just as bad and was still missing my wanted features so I set it back to true.

 I then tried removing ubuntu's Firefox from the package manager via sudo apt-get purge Firefox and then installing the package from Firefox's download page via dpkg -i. But it still persists to use the same cruddy file picker. Also I noticed this was a different Firefox due to the tool menu being hidden and having it only show via the alt key.

 And my last resort was trying to use firefox-kde-helper from this webpage: [https://launchpad.net/~blue-shell/+archive/ubuntu/firefox-kde](https://launchpad.net/~blue-shell/+archive/ubuntu/firefox-kde). I installed fine but the file dialogue remains the same... I even had dolphin already installed. Which then I tried setting dolphin to the default file manager by [https://sites.google.com/site/installationubuntu/tweaking-ubuntu/change-default-filemanager](https://sites.google.com/site/installationubuntu/tweaking-ubuntu/change-default-filemanager). However it still did not work.
 


 So could anyone help me change this darn file picker? Also, how does Canonical let such a thing like these features slip by?

---

