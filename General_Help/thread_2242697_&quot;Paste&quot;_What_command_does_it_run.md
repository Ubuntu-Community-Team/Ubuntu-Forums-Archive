---
title: "&quot;Paste&quot; What command does it run?"
date: 2014-09-03
forum: General Help
---

### Post by viking777 on 2014-09-03
I am using Thunar on xubuntu, but it makes no difference, every filemanager on every distro has an entry in the context menu called 'Paste'. Now I am fully aware of what it does, but I would like to know how it is doing it. Every gui program on linux simply runs underlying commands, but what command is the menu item 'Paste' actually running? It certainly isn't the linux command ```
paste
``` because that does something completely different. 

Why do I want to know? 

Well I would like to create an alternative 'Paste' menu entry (via Thunar custom actions) entitled 'Paste as root', which would in theory, only require me to prepend the 'Paste' command with 'sudo' to get what I want. But the command behind the 'Paste' button seems to be a state secret that I cannot find. 

Anyone know the answer?

BTW the answer is definitely not ```
sudo cp something somewhere
``` and it is definitely not ```
gksudo thunar
``` either.

---

### Post by mcduck on 2014-09-03
Sorry to tell you, but no, there is no single underlying "paste" command, and neither is *every* GUI program just a pretty skin for terminal commands (even though many of them have either command-line interface or there is a CLI program for the same purpose).

Especially at the point when you go beyond the simple concept of copy/pasting text, and start dealing with pictures, files etc, the copy/paste quickly becomes a feature of the program used to do it rather than just implementing some common Linux- or desktop environment feature.

What comes to the specific example of copy/paste for files you mentioned, the commands to do it would indeed be *cp* and *mv*, even though the file manager doesn't actually do it by running those shell commands.

---

### Post by viking777 on 2014-09-03
OK, thanks for that mcduck - that probably explains why I can't find an answer myself then.

---

### Post by mcduck on 2014-09-03
yeah, I think it would explain the difficulty pretty well. :D

Anyway, I'd think for a custom "paste as root" you could indeed use the "cp" command. I havent' used XFCE that much myself, but I'd assume Thunar does something similar to what Nautilus does and gives you the selected file(s), current directory and other things as variables you can then use in your own scripts...

this might be helpful:[http://www.linux.com/learn/tutorials/440846-extend-xfces-thunar-file-manager-with-custom-actions]("http://www.linux.com/learn/tutorials/440846-extend-xfces-thunar-file-manager-with-custom-actions")

---

### Post by vasa1 on 2014-09-03
> **mcduck said:**
> ...
this might be helpful:[http://www.linux.com/learn/tutorials/440846-extend-xfces-thunar-file-manager-with-custom-actions]("http://www.linux.com/learn/tutorials/440846-extend-xfces-thunar-file-manager-with-custom-actions")
Bookmarked it!

---

### Post by dgriffiths on 2014-09-03
Dunno if it helps any, but here's the code Thunar uses to process a "Paste" request...

```
static void
thunar_standard_view_action_paste (GtkAction          *action,
                                   ThunarStandardView *standard_view)
{
  ThunarFile *current_directory;

  _thunar_return_if_fail (GTK_IS_ACTION (action));
  _thunar_return_if_fail (THUNAR_IS_STANDARD_VIEW (standard_view));

  current_directory = thunar_navigator_get_current_directory (THUNAR_NAVIGATOR (standard_view));
  if (G_LIKELY (current_directory != NULL))
    {
      thunar_clipboard_manager_paste_files (standard_view->clipboard, thunar_file_get_file (current_directory),
                                            GTK_WIDGET (standard_view), thunar_standard_view_new_files_closure (standard_view, NULL));
    }
}
```

---

### Post by viking777 on 2014-09-04
Thanks for those replies people I would have replied earlier, but I got no notifications of the responses, sorry, don't know why.

Anyway as it happens the replies weren't needed as I managed to solve the underlying problem - how to paste as root in thunar without using a root instance of the file manager - without the need to understand the Thunar 'Paste' command

If you want a Thunar custom action for 'Paste as Root' this is it:

```
sudo cp -r `xclip -o` %f
```

It looks very simple when you look at it like that, but it took me a lot of effort to get there. Of course to make it work you need xclip installed and also, before you click 'Paste as Root' shortcut make sure that the file you want to paste is the first item in the clipboard. It works for files and directories, but not as yet for multiple files/directories. 

If you wonder why I want this, it is because my beloved filemanager 'Spacefm' (which has all these commands and a million others built in by default) has been dropped by its developer and is no longer maintained, so I need to investigate some alternative and Thunar isn't bad and is already part of Xfce which is my desktop of choice.

Thanks again for the replies.

Edit. If you are thinking of trying this out, I would hold fire for a while. It works perfectly on Linux Mint (which was what I was testing it on) but I can't get it to work on my other two distros Ubuntu and Manjaro - yet. Also it only works on Mint if you are within the sudo timeout, it doesn't offer a password entry dialogue if you are outside of that, so maybe it isn't solved after all. I will keep at it though.

---

### Post by viking777 on 2014-09-04
I never fail to be amazed at how unobservant (read - dumb) I can be. The reason it wouldn't work in Ubuntu and Manjaro was purely down to typos, but it took me hours to see them! On one I had forgotten to type 'sudo' and on the other I had typed ampersand instead of percentage :shock: Anyway, if you aren't as stupid as me this command does work. You have to have done something as sudo first though - and I don't know the answer to that, but I did figure out  the multiple files question - substitute %f with %F. 

Jees, by the time I have finished with Thunar it will be nearly half as good as Spacefm. The dev must have had a nervous breakdown to ditch the best program in the linux ecosystem today to go and work on BSD - which is what he has done. 

Anyway I am marking this as 'solved' again and then I am off to work on 'Rename as Root' next :D

---

### Post by mcduck on 2014-09-04
try using "gksudo" instead of "sudo" (I'd assume it's installed by default in Xubntu but of not just get it from the repositories). It'll give you a GUI window to type in your password...

---

### Post by viking777 on 2014-09-04
> **mcduck said:**
> try using "gksudo" instead of "sudo" (I'd assume it's installed by default in Xubntu but of not just get it from the repositories). It'll give you a GUI window to type in your password...

I'll try that mcduck. In the meantime 'Rename as Root' was a piece of cake:

```
sudo mv %f  `zenity --entry`
```

Only tested on Ubuntu so far, but it looks good. Obviously you need 'zenity' installed.

I will try that with gksudo as well and report back.

---

### Post by viking777 on 2014-09-04
You are right enough in saying that gksudo launches the password entry dialog box, trouble is, it won't run the command that follows it. I have tried backticks, pipes, double ampersands, apostrophe's, quote marks, and combinations of those, but nothing loads the command you need to run. I guess the Thunar custom actions dialog works differently to the terminal. 

Anyway, I have had enough for today, I will look at it again tomorrow.  

Thanks for the suggestion.

Edit. Ignore everything above, I rebooted and now it seems to work properly (with "" bracketing the command)?? 

As I said I will look into it again tomorrow, but it seems I have the answer.

---

