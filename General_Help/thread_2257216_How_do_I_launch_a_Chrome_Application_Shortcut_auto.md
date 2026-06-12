---
title: "How do I launch a Chrome Application Shortcut automatically when the OS loads up?"
date: 2014-12-17
forum: General Help
---

### Post by ryan128 on 2014-12-17
The computer is only going to be used to display a webpage and I would like it to open automatically when the system turns on. I also want it to open with the window size maximized or automatically go into fullscreen mode(F11).

And I only have about a few hours experience using Linux. So keep that in mind...

Any help is appreciated!

---

### Post by Dennis N on 2014-12-17
Lubuntu 14.04:

1) Set the web page you want to open as the home page. 
2) Add Chrome to your startup applications in Preferences > Default Applications for LXSession > Autostart Tab > Manual Autostarted Applications
The program should open maximized if it was maximized when last closed, so be sure that is the case.

---

### Post by ryan128 on 2014-12-18
[https://support.google.com/chrome/answer/95710?hl=en](https://support.google.com/chrome/answer/95710?hl=en)

I'm using a shortcut created using the second method. So setting the webpage to my home page wont work. Unless I can make it go into the F11 fullscreen mode automatically, then it would work. I just need to know how to automate it.

And for whatever reason when I open the shortcut the window is only slightly larger than your profile picture. Even if the window is maximized before being closed.

---

### Post by vasa1 on 2014-12-18
If you're using default Lubuntu, you should have this file: ~/.config/openbox/lubuntu-rc.xml

You can edit it to make any application always open fullscreen, not maximized.

Back up lubuntu-rc.xml.
Open lubuntu-rc.xml using a plain text editor.
Go down to the very end of the file. You should see these three lines:```
    </application>
  </applications>
</openbox_config>

```Place your cursor at the start of the second line, </applications>, and hit enter a few times.

Paste the following code into the blank space:```
    <application name="Google-chrome">
      <fullscreen>yes</fullscreen>
    </application>

``` so that the end of the file looks like this:```
    </application>
    <application name="Google-chrome">
      <fullscreen>yes</fullscreen>
    </application>
  </applications>
</openbox_config>

```
Remove any extra blank lines (optional).
Save the file.

Open a terminal and run```
openbox --reconfigure
```You should not see any pop-up and you should just get back the terminal prompt. If you do see any pop-up, it means you've messed up somehow :)

Now, when you open Google Chrome it should always open fullscreen.

---

### Post by vasa1 on 2014-12-18
In my opinion, you don't need to mess with apps.

Instead of having just **google-chrome** in your autostart, use **google-chrome [http://www.whatever.com](http://www.whatever.com)** or, if it's a local file use **google-chrome file:///path/to/file**. For example, my Google Chrome opens to **file:///home/vasa1/Dropbox/MyLinks.html**

Or, you could go into the browser's settings and do the needful there:

---

### Post by CantankRus on 2014-12-18
Open your desktop shortcut with your text editor. (You may be able to right click and "open with" in the file browser in Lubuntu or open the text editor > open file and browse to your desktop)
Change the exec line.
eg I used chrome to create a shortcut for ubuntuforums which gave me this exec line...
```
Exec=/opt/google/chrome/google-chrome [COLOR="#FF0000"]--app=[/COLOR]http://ubuntuforums.org/
```
I removed the [COLOR="#FF0000"]--app=[/COLOR] and added [COLOR="#FF8C00"]--kiosk[/COLOR] to open fullscreen.
```
Exec=/opt/google/chrome/google-chrome [COLOR="#FF8C00"]--kiosk[/COLOR] http://ubuntuforums.org/
```

Clicking on the desktop shortcut opens in fullscreen.

In ubuntu I can then just add the exec command to autostart applications...
```
/opt/google/chrome/google-chrome --kiosk [COLOR="#EE82EE"]**http://ubuntuforums.org/**[/COLOR]
```
Use [COLOR="#EE82EE"]**your url**[/COLOR].

---

### Post by ryan128 on 2014-12-18
Thanks for the ideas.

It appears that the "kiosk" feature is exactly what I need. And after a quick Google search there are all kinds of tutorials on how to set it up.

---

