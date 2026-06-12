---
title: "create usplash theme"
date: 2008-05-10
forum: General Help
---

### Post by Arutha on 2008-05-10
I use Hardy Heron Ubuntu, and I installed usplash and libusplash-dev and startup-manager. I want to make my own usplash theme.

In my /usr/share/doc/libusplash-dev/examples directory, there are instructions on how to do this. First, I simply did:
```
sudo make
sudo make install
```
so that the eft-theme.so file was created in /usr/lib/usplash

I then used the startup-manager to change the usplash theme to the newly created one, and I changed resolution to 800x600 and color depth to 8bit. But even that example theme doesn't work: I only see a black screen, and the progress bar is white.

I also tried the utility MakeUsplash from TheeMahn, it doesn't seem to work either (same problem).


Does this mean that usplash themes don't work in Hardy Heron at all? Did they change something about usplash from Gutsy to Hardy? Does anyone know where to find detailed information on how to create usplash themes in Hardy Heron?

---

### Post by Arutha on 2008-05-13
has anyone succeeded in making a usplash theme that works in Hardy Heron?

---

### Post by priegog on 2008-06-16
I tried the MakeUsplash script too, but all the colors turn out wrong...

---

### Post by Joe Kuan on 2009-06-04
I am not sure whether this helps. 

First, you need to make sure your splash image has 8 bits colormap. To check that run 'file <image.png>'. If not, then you can use 'convert' to convert it to 8 bits colormap. See [http://joekuan.wordpress.com/2009/05/26/how-to-create-8-bit-colormap-png-image-for-usplash/]("http://joekuan.wordpress.com/2009/05/26/how-to-create-8-bit-colormap-png-image-for-usplash/")

Secondly, make sure that your color index value in your theme.c file is pointing to the correct color in the colormap of your splash image. You can display the colormap from GIMP. See [http://joekuan.wordpress.com/2009/06/02/how-to-easily-experiment-your-new-usplash-theme-from-a-terminal/]("http://joekuan.wordpress.com/2009/06/02/how-to-easily-experiment-your-new-usplash-theme-from-a-terminal/") 

Finally, you don't need to use Startup-Manager to test your splash theme. It is much easier to use command line utilities 'usplash' and 'usplash_write'. See the above link. Once you got everything right, then we can either use 'update-alternatives' or Startup-Manager to install the new theme.

Hope this helps
Joe

---

### Post by DJ_Peng on 2009-06-13
Thanks for posting those links, Joe. I had created Usplashes that worked for Intrepid (and I think Hardy as well) but Jaunty versions always fail. I'm going to check out those posts and see if I can finally get it to work.

---

