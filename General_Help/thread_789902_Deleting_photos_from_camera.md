---
title: "Deleting photos from camera"
date: 2008-05-10
forum: General Help
---

### Post by yang on 2008-05-10
I can import photos to f-spot from my camera fine, but how do I manage the photos (files) on the camera itself?  For instance, I'd like to delete some photos.  I looked in Nautilus under /media and in 'Computer', but didn't see the camera.  Any hints?  Thanks in advance.

---

### Post by bmac on 2008-05-11
I prefer to use G Thumb Image Viewer as my camera download application for that very reason. To try G Thumb simply connect your camera and close F Spot when it opens and open G Thumb (Should be in apps/graphics if not edit your menu it may be unchecked). Once G Thumb opens select file/import photos. An import photos popup box appears - if your camera doesn't appear in the camera icon simply click on icon and select your camera. Should you wish to use G Thumb as your camera application permenantly open file manger select edit/prefrences/media and change Photos to G Thumb...

Hope this helps...

---

### Post by unutbu on 2008-05-11
To delete all photos, you could open a terminal and type (or for ease of use save the command in a script):

```
gphoto2 --port usb --camera "<model>" -D
```

Replace <model> with the model of your camera. 

If you are not sure what to put for <model>,
```
gphoto2 --list-cameras
```
will list all supported cameras. 

To download all pictures:
```
gphoto2 --port usb --camera "<model>" -P
```

There is also a way to delete individual pictures from the command-line, but I wouldn't recommend it. It's easier to use the camera's interface to delete pictures. For that matter, you might find it easier to delete all pictures using the camera's interface.

If the camera does not provide an option to delete all pictures, look for an option to format the memory card. This can be quicker and it accomplishes the same thing.

---

