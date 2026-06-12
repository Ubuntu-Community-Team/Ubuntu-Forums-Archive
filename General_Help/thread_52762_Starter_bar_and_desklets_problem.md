---
title: "Starter bar and desklets problem"
date: 2005-07-28
forum: General Help
---

### Post by umdzig on 2005-07-28
I just recently decided to get rid of windows completely and move to Ubuntu. I have 2 problems;

My first problem is when i create a new starter for the starter bar widget with gdesklets. I am trying to create a link to my user directory however nothing happens when i click the starter that should take me to my user directory. I tried typing /home/zig (zig is my username) and said it was a link, i even tried creating a laucher on my desktop and dragging it over to the starter bar, however as i mentioned before nothing happens.

My second problem is with gdesklets. Everytime i try to use a widget that will show the status of my cpu usage or temperature i get an error saying "Error in sensor CPU".

If anyone could help i would appreciate it! Thanks in advance.

---

### Post by autocrosser on 2005-07-28
Well as to the first problem--use Synaptic & download Gtweekui--it includes a tweek for Nautilus--allows you to have trash, home directory & several other options on your desktop--

You can also just open a Nautilus window & drag'n'drop your home directory in a panel--it will create a link automatically--

As to the sensors prob--you need to download lm (ln?)sensors --use Synaptic for that one also--And there are several good threads on howto set the sensors up--

Glad to hear you ditched Windoze--I'm converting people over as fast as I can--once you see how easy it "really" is--you won't go back!!!

---

### Post by umdzig on 2005-07-28
Ok i have installed the lm sensors...thanks for the tip i'll play around with them and ill follow the how to you said to find. 

I cant seem to find the Gtweekui you said to find in synaptic. I might not have the correct repository list (I installed the one the ubuntu beginner guide i found) could you post a copy of your repository list? 

I also tried opening a nautilus window and drag and drop your home directory in a panel and that did nothing but freeze up the starter bar widget.

---

### Post by OneSeventeen on 2005-07-28
I just found it, it is gtweakui, and it is a huge help on configuring gnome.

I too just switched from windows, and I'm actually enjoying it so far.

---

### Post by umdzig on 2005-07-28
I have installed gtweakui and had it show the computer icon etc. However i still cant get them to create a link when i drag them to the starter bar. Is this a bug or should i reinstall gdesklets because i have found out in other threads that gdesklets from the repository list in synaptic is buggy and it says i should install it directly. If i do this can someone show me how to install any file i download from the internet. I know this is a noob question but i have only used synaptic and followed how to guides.

---

### Post by matthew on 2005-07-28
Check these two threads (read them both before you do anything) for more info on how to get and run the latest gDesklets.

[http://www.ubuntuforums.org/showthread.php?t=31928](http://www.ubuntuforums.org/showthread.php?t=31928)
[http://www.ubuntuforums.org/showthread.php?t=40982](http://www.ubuntuforums.org/showthread.php?t=40982)

---

### Post by autocrosser on 2005-07-29
[QUOTE=umdzig]I have installed gtweakui and had it show the computer icon etc. However i still cant get them to create a link when i drag them to the starter bar. Is this a bug or should i reinstall gdesklets because i have found out in other threads that gdesklets from the repository list in synaptic is buggy and it says i should install it directly. If i do this can someone show me how to install any file i download from the internet. I know this is a noob question but i have only used synaptic and followed how to guides.[/QUOTE]

There are stupid answers, but if you don't know it--it's not a stupid question :wink: 
The easy way to add a link to one of the panels---

1. Open a Nautilus browser window
2, find the file (directory) you want to add to a panel
3 Drag'n'drop the directory on the panel you want--
You'll see a "folder" icon on the panel--right-click to change the icon/view properities/move it/delete it---

That's it--Much easier than Windoze :grin:

---

### Post by austinz on 2005-08-07
This may or may not be related.  I'm running the lated gdesklets and breezy, and can get gdesklets loaded and running.  However, 75 percent of the desklets don't start, with a log message of:

```
Log messages of /home/austin/.gdesklets/logs/gdesklets%3A0.0.log                     
==========================================================[08/07/05-11:30:15]===     
Adding "/home/austin/.gdesklets/Displays/GnomeBar-2.0.2/GnomeBar.display" with ID    
"id11234286147550118" to the desklet list.                                           
==========================================================[08/07/05-11:30:16]===     
=== Runtime Error                                                                    
No module named bonobo.ui                                                            
/usr/lib/gdesklets/utils/ErrorFormatter.py                                           
  118 # give us an absolute path.                                                    
  119 #                                                                              
  120 _old_imp = __import__                                                          
  121 def _new_imp(name, globs = {}, locls = {}, fromlist = []):                     
  122                                                                                
> 123     module = _old_imp(name, globs, locls, fromlist)                            
  124     # builtin modules have no "__file__" attribute, so we have to check for it 
  125     if (hasattr(module, "__file__")):                                          
  126         module.__file__ = os.path.abspath(module.__file__)                     
  127     return module                                                              
  128                                                                                
  129 import __builtin__                                                             
==========================================================[08/07/05-11:30:16]===     
Removing "/home/austin/.gdesklets/Displays/GnomeBar-2.0.2/GnomeBar.display" with ID  
"id11234286147550118" from the desklet list.                                         
==========================================================[08/07/05-11:30:16]===     
=== Unhandled error! Something bad and unexpected happened.                          
first parameter must be a GdkWindow                                                  
in /usr/lib/gdesklets/utils/__init__.py: line 150 f                                  
in /usr/lib/gdesklets/display/Window.py: line 525 __set_window_flags                 
in /usr/lib/gdesklets/display/Window.py: line 426 set_layer                          
in /usr/lib/gdesklets/display/GlassWindow.py: line 225 _set_flag_managed             
in /usr/lib/gdesklets/display/GlassWindow.py: line 210 _set_type_hint_dock           
/usr/lib/gdesklets/display/GlassWindow.py                                            
  205                                                                                
  206                                                                                
  207                                                                                
  208     def _set_type_hint_dock(self, window, value):                              
  209                                                                                
> 210         x11.set_type_dock(window, value)                                       
  211                                                                                
  212         #value and window.set_type_hint(gtk.gdk.WINDOW_TYPE_HINT_DOCK) or \    
  213         #          window.set_type_hint(gtk.gdk.WINDOW_TYPE_HINT_NORMAL)       
  214                                                                                
  215                                                                                
  216                                                                                
==========================================================[08/07/05-11:30:16]===     
=== Unhandled error! Something bad and unexpected happened.                          
'TargetImage' object has no attribute '_TargetImage__widget'                         
in /usr/lib/gdesklets/utils/__init__.py: line 150 f                                  
in /usr/lib/gdesklets/display/TargetImage.py: line 160 __render_image                
/usr/lib/gdesklets/display/TargetImage.py                                            
  155         #if ((imgwidth, imgheight, saturation, opacity) ==                     
  156         #    (self.__current_width, self.__current_height,                     
  157         #     self.__current_saturation, self.__current_opacity)):             
  158         #    return                                                            
  159                                                                                
> 160         self.__widget.render(imgwidth, imgheight, opacity, saturation)         
  161         self.__current_width = imgwidth                                        
  162         self.__current_height = imgheight                                      
  163         self.__current_opacity = opacity                                       
  164         self.__current_saturation = saturation                                 
  165                                                                                
  166                                                                                
==========================================================[08/07/05-11:30:16]===     
=== Unhandled error! Something bad and unexpected happened.                          
'TargetImage' object has no attribute '_TargetImage__widget'                         
in /usr/lib/gdesklets/utils/__init__.py: line 150 f                                  
in /usr/lib/gdesklets/display/TargetImage.py: line 160 __render_image                
/usr/lib/gdesklets/display/TargetImage.py                                            
  155         #if ((imgwidth, imgheight, saturation, opacity) ==                     
  156         #    (self.__current_width, self.__current_height,                     
  157         #     self.__current_saturation, self.__current_opacity)):             
  158         #    return                                                            
  159                                                                                
> 160         self.__widget.render(imgwidth, imgheight, opacity, saturation)         
  161         self.__current_width = imgwidth                                        
  162         self.__current_height = imgheight                                      
  163         self.__current_opacity = opacity                                       
  164         self.__current_saturation = saturation                                 
  165                                                                                
  166                                                                                

```

I've got the bonoboui deb installed, but still nothing works.  Any suggestions?

Thanks for the help!

AUstin

---

