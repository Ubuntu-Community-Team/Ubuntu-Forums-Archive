---
title: "Open password protected  document without having to do so manually"
date: 2020-07-25
forum: General Help
---

### Post by raleigh3 on 2020-07-25
I have an .odt document that is password protected.

I am using LibreOffice.

Is there a way to open it without having to manually supply the password every time?

Security is not an issue as I am the only person with access to my computer.

---

### Post by TheFu on 2020-07-25
Yes. Remove the password. [https://ask.libreoffice.org/en/question/146051/remove-file-password-protection/](https://ask.libreoffice.org/en/question/146051/remove-file-password-protection/) explains how.

---

### Post by raleigh3 on 2020-07-25
I still want to keep the password.

---

### Post by Holger_Gehrke on 2020-07-26
According to this post on [askubuntu]("https://askubuntu.com/questions/1061571/open-swriter-password-protected-file-from-command-line"), passing a password on the command line has been on the list of requested features for LO / OO for a long time. There are functions to open a document with a password in StarBasic and in the UNO-libraries used for writing macros for LO / OO in other languages. So you'd need a macro to do this.

Holger

---

### Post by raleigh3 on 2020-07-29
> **Holger_Gehrke said:**
> According to this post on [askubuntu]("https://askubuntu.com/questions/1061571/open-swriter-password-protected-file-from-command-line"), passing a password on the command line has been on the list of requested features for LO / OO for a long time. There are functions to open a document with a password in StarBasic and in the UNO-libraries used for writing macros for LO / OO in other languages. So you'd need a macro to do this.

Holger

Could you please help me with the macro I would need?

Thanks,
            Andy

---

### Post by TheFu on 2020-07-29
> **raleigh3 said:**
> Could you please help me with the macro I would need?

Thanks,
            Andy

I'm guessing just an **xdotool** macro would work. You'd still need to press a button chord to cause it to be entered. There are a few others, but xdotool can be tied to accel key chords to be entered into any textentry field.

The script would open the file, see the password entry box, enter the password. An example:
[https://medium.com/daniels-tech-world/using-xdotool-at-and-bash-to-automate-netflix-and-youtube-viewing-on-linux-5ae62185d1c](https://medium.com/daniels-tech-world/using-xdotool-at-and-bash-to-automate-netflix-and-youtube-viewing-on-linux-5ae62185d1c)
The YT link: [https://www.youtube.com/watch?v=dXHdpz9QA7M](https://www.youtube.com/watch?v=dXHdpz9QA7M)

Be careful using any "mouse move" stuff that is absolute coords.  Try to use the active window method. I don't have an exact example, but do have one that looks for the window titled as "Chromium", then presses the F11 key (go fullscreen in the browser).
```
xdotool search --sync --onlyvisible --class "Chromium" windowactivate key F11
```
 That is part of a script that I use for presentations - so I only need to run 1 command to have a presentation start, load the correct files, and become full screen.

---

### Post by dragonfly41 on 2020-07-29
I also use Actiona for such automation bots.  Actiona is found in repo.  ```
sudo apt install actiona
```
I do not claim that it is easy to understand or use since it requires some reading about actionscript2 (an ageing language with Flash origins).
But once mastered Actiona can be very useful. For example I am integrating such bots into a tutorial using links (actiona:// url protocol handler).
So a presentation might have a hyperlink to run a command (security precautions aside)
Actiona can also run detached commands such as xdotool to add to its functionality.

The idea is to break away from YouTube presentations and go for *interactive* HTML5 tutorials where the target application can be driven from the presentation in parallel sessions. 

In this case Actiona script could prompt user for a password then launch LibreOffice Writer and paste in the password to open the designated password protected document.  Actiona script can also download the document and place it in filesystem ready to be opened.

If users had Actiona installed we could just post bots to be run by users rather than the copy and paste exercises we go through in forum posts. This might help a lot in diagnosing common issues such as dual boot.  But the bots (scripts) would need to be trusted! 

[Added note}Perhaps a trusted bot repository might be useful.

---

### Post by Holger_Gehrke on 2020-07-29
Open LO, select 'Tools', 'Macros', 'Organize Macros', 'LibreOffice Basic'. Create a library and a module. Edit the module and enter the following Basic-source:
```

Sub OpenFileWithPW(filename as string,pw as string)
  Dim FileProperties(1) As New com.sun.star.beans.PropertyValue
  Dim Doc as Object
  
  FileProperties(0).Name="Password"
  FileProperties(0).Value=pw
  Doc=StarDesktop.loadComponentFromUrl(ConvertToURL(filename),"_blank",0,FileProperties())
End Sub

```

Now you can call this macro from the command line:
```

lowriter 'macro:///library.module.OpenFileWithPW("filename","pw")'

or on my system, with my library and module with a test document with password test:
lowriter 'macro:///Standard.Module1.OpenFileWithPW("/home/holger/Unbenannt 1.odt","test")'

```
Giving the full path to the file might be important, in all cases where I tried to use just a filename I got some error.

Holger

---

### Post by HermanAB on 2020-07-30
That is an interesting security hole that you are trying to make there.

---

### Post by TheFu on 2020-07-30
> **HermanAB said:**
> That is an interesting security hole that you are trying to make there.

But he doesn't care about security ... yet wants a password?
> Security is not an issue

Security is always an issue on any networked device, but it is his stuff.  We all probably do less than brilliant things from time to time. That includes me. ;)

---

### Post by raleigh3 on 2020-08-09
> **HermanAB said:**
> That is an interesting security hole that you are trying to make there.

No security hole when I am the only one with access to my computer.

---

### Post by raleigh3 on 2020-08-09
I did what you suggested.

```
Sub OpenFileWithPW
  Dim FileProperties(1) As New com.sun.star.beans.PropertyValue
  Dim Doc as Object
  
  FileProperties(0).Name="my password"
  FileProperties(0).Value=pw
  Doc=StarDesktop.loadComponentFromUrl(ConvertToURL(/home/andy/Documents/New_Journal.odt),"_blank",0,FileProperties())
End Sub
```

Nothing happens when I run

```
lowriter 'macro:///library.module.OpenFileWithPW("/home/andy/Documents/New_Journal.odt","my pasword")'
```

I am not sure if I created a library?

---

### Post by Holger_Gehrke on 2020-08-09
Take a look at the attached screenshot of the Libre Office macro editor. See the panel on the left ? It shows the Libraries and Modules. You can think of them as directories and files, although the real structure behind it is actually a bit more complicated. When calling a macro from the command line with a 'macro://'-URI you have to give the names of the library and the module, otherwise LO won't find the code. Since AFAIK you can't have code outside of a module or a module outside of a library, it should be just a matter of finding where you put it and giving the right names in the command.

It might be a good idea to simplify matters by putting that long command into a shell script that takes file name and password as parameters and builds the right command from those. If you make the name of that script short enough, you could get into the habit of putting a space at the beginning of the command so it doesn't get stored in the shell's history, which would lessen the security problem.

Holger

Edit: just read through the code you posted and noticed you tried to change some things, specifically you removed the parameter definitions and changed the value assigned to 'FileProperties(0).name'. That's not the password stored there, that's the name of the property. If it's not 'Password' it won't work. The actual password is passed as a parameter named pw from the command line call to the macro and then assigned to FileProperties(0).value. You could get away with hard-coding the password and setting a fixed file name and removing the parameters, put then you have to leave them out of the macro-call, too. So then it should be something like ```

lowriter 'macro:///library.module.OpenFileWithPW'

```
and you need quotes around the hard-coded file name, since the function ConvertToURL expects a string as its parameter.

---

### Post by HermanAB on 2020-08-10
"No security hole when I am the only one with access to my computer."  Please ensure that you use 'whole disk' encryption then. The trouble is that computers get stolen, old disk drives get resold...

---

