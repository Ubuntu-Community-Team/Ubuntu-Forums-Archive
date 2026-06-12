---
title: "Websites and Cookies"
date: 2014-04-24
forum: General Help
---

### Post by Stob on 2014-04-24
I used Firefox all the time, pre-Ubuntu. Now that I'm using Ubuntu and Firefox, websites will not keep login info, and each time I have to type in my user name and PW. I'm not talking secure type websites, just every day forums and such. Is there a setting somewhere?

---

### Post by Impavidus on 2014-04-24
Edit &#8594; preferences &#8594; privacy. You can change the cookie settings.

---

### Post by SeijiSensei on 2014-04-24
The first time you log into a site, Firefox will pop up a box asking you if you want it to store your credentials.  Does that box not appear for you?  Look in Edit > Preferences > Security and make sure the "Remember passwords for sites" box is checked.

Storing your credentials has nothing to do with "cookies."  Those are small files stored on your computer that contain information the web site developer wants to store on your machine.  Often cookies are benign and vital to the operation of sites that need to track users during a session.  This site uses cookies for that purpose.  Once you log in, a cookie is stored on your computer that identifies you as an authorized user so you can move from page to page without having to log in repeatedly. 

Other cookies are less benign and are often used to report your browsing patterns to third-party advertising sites.  I use the [Ghostery]("http://www.ghostery.com/") add-on for Firefox to handle these types of cookies.  You can block or accept such cookies on the fly.  

You can see all the cookies stored on your machine using Edit > Preferences > Privacy.  If you disable cookies entirely some sites will not work correctly.  You might choose to disable "third-party" cookies, however, since those are the ones most likely being used to track your behavior.

---

### Post by Stob on 2014-04-24
I never had a popup about credentials. However, going to "security", the "remember passwords for sites" is not highlighted, it is dim and cannot be checked. But, the box below that "show passwords" I can click and it has all the websites, user names and passwords stored. So, why will they not convey to the websites?

---

### Post by SeijiSensei on 2014-04-24
Do you have the "master password" box checked as well?  You may not be able to change anything without that if you use a master password.  If you don't, it might be a permissions issue.

Your Firefox profile is stored in a "hidden" directory in your home called .mozilla.  Usually these files and directories are not displayed, but you can tell a file manager like Nautilus or Dolphin to show those files with a keystroke, often Alt+period, or by looking in the menus for the appropriate command.

You should make sure that everything in the .mozilla directory is owned by your account.  If you're comfortable with the terminal, use this approach (I'll assume your username is "stob").  First, close Firefox using File > Quit.  That ensures that any child windows like the Bookmark Manager are closed as well.  Then open a terminal and type:
```

cd ~
chown stob:stob -R .mozilla
chmod u+w -R .mozilla

```
That will make everything in .mozilla directory is owned by you.  For good measure, I included the command to make everything in that directory writable by you as well.  Restart Firefox.  Is the box still greyed out?

If that doesn't fix the problem, close Firefox, rename .mozilla to .mozilla.old, then restart Firefox. You'll now have a clean profile. I recommend you use Bookmarks > Show All Bookmarks > Import and Backup > Backup first to make a copy of your bookmarks.  You can then use the same utility to restore the bookmarks from the file you saved.  You may able to copy over your passwords as well.  Take a look at the Firefox documentation or search the Internet for that.

---

