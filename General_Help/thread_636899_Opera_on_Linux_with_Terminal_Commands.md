---
title: "Opera on Linux with Terminal Commands"
date: 2007-12-10
forum: General Help
---

### Post by Sugi on 2007-12-10
I have opera installed and I love this app, but I want to do some commands within the terminal with opera.  All I have found out so far is:

open opera
$ opera

open new tab
$ opera -newpage

open new tab with url address
$ opera -newpage [www.google.com](www.google.com)

change current tab's url address
$ opera [www.google.com](www.google.com)

My question is, 
 - is there a command for closing a tab in opera?  
 - is there a command for exiting opera all together?  
 - Is there command for opening opera without holding it to the terminal box (if you use the command within the terminal "$ opera" it will open opera, but if you close that terminal box it will shut down opera as well.   is there a away around that?)

By the way,  I have looked within the opera website and typed "$ opera help" in the terminal, but it doesn't give me any commands for opera within the terminal.  Can anyone help me out here?


Sugi

---

### Post by meborc on 2007-12-10
the best way to get that kind of info is to look at the man pages
```
man opera
```:)

i have no idea if that is what you were looking for, but it sure lists some operators you can use with the opera command

---

### Post by Sugi on 2007-12-10
just type "$ man opera" or look at the main pages of opera.com?  Im kinda confuse here. >.<

---

### Post by Sugi on 2007-12-11
#opera --help
> Usage: opera [options] url

  -newwindow                     open url in new window
  -newpage                       open url in new page (tab)
  -backgroundpage                open url in background page (tab)
  -fullscreen                    start in full screen mode
  -iconic                        start in iconic mode
  -geometry <geometry>           set geometry of toplevel window
  -remote <command>              send command to another Opera window
  -noraise                       do not raise window when receiving a remote command
  -window <window id>            a remote opera window
  -windowname <window name>      a remote opera window with a symbolic name
  -restore                       restore default interface
  -nosession                     do not open saved window sessions or homepage
  -nowin                         do not open any document windows
  -nomail                        start opera without internal e-mail client
  -noshape                       do not apply shape to widgets
  -language <file>               use translation from specified file
  -binarydir <path>              location of version-specific binaries
  -personaldir or -pd <path>     location of alternative '.opera' directory
  -display <displayname>         set the X display
  -fn <font>                     set the normal text font
  -bg <color>                    set the background color
  -fg <color>                    set the foreground color
  -visual TrueColor              use TrueColor visual on an 8-bit display
  -cmap                          use private color map on an 8-bit display
  -smallicon                     use a smaller icon image
  -notrayicon                    do not show an opera icon in system tray
  -disableinputmethods           disable input methods
  -restoreextensions             restore default file type extensions
  -postfix <name>                append name to WM_CLASS and WM_WINDOW_ROLE
  -version                       show version data
  -full-version                  show version data and build details
  -kioskhelp                     extra options for kiosk mode operation
  -debughelp                     extra options for simple debugging
  -help or -h                    show this help

Remote commands:
  openURL()                      open "Go to" dialog box prompting for input
  openURL(url)                   open url in active window
  openURL(url,<destination>)     open url in destination <W|P|B>
  openFile(<destination>)        open file selector in destination <W|P>
  openM2(<destination>)          open M2 list view in destination <W>
  openComposer(<destination>)    open M2 composer in destination <W>
  addBookmark(url)               add url to bookmark list
  raise()                        raises the opera window
  lower()                        lowers the opera window

  <destination> Replace W: new-window, P: new-page, B: background-page

  A standalone url argument or '-newwindow', '-newpage', '-backgroundpage'
  or '-nowin' will disable '-remote' commands

Notes:
  * <geometry> format is: WIDTHxHEIGHT+XOFF+YOFF
  * '-window' and '-windowname' work for '-remote' and '-newwindow' commands
  * '-window' accepts hexadecimal (default) or a decimal argument
  * '-fullscreen' works when a new browser is launched
  * '-nowin' disables any url argument
  * '-windowname' will override '-newwindow' if a named window is located
  * '-noraise' works for remote commands that do not open a dialog box


#man opera
> OPERA(1)                                                              OPERA(1)

NAME
       opera - a standards-compliant graphical Web browser

SYNOPSIS
       opera [options] [URL...]

DESCRIPTION
       Opera  is  a graphical Web browser available on several platforms.  The
       desktop version described  in  this  manual  page  runs  on  GNU/Linux,
       FreeBSD,  and  Solaris.   Versions  for  Macintosh and Windows are also
       available.

COMMAND LINE OPTIONS
       These support both double and single dash  as  prefix.   Several  other
       options  are  also  supported, notably including many generic X Toolkit
       options; see --help output for details.

       --personaldir path

       --pd path
              Use path as personal  configuration  directory  (ignore  default
              location).

       --remote command
              Send command to an existing Opera window.  See "REMOTE COMMANDS"
              section below.

       --nomail
              Start Opera without internal e-mail client (also  disables  chat
              and newsfeeds).

       --nosession
              Do not open a saved window session or homepage.

       --noshape
              Suppress  X  shape-extension  for  widgets,  to  make their full
              underlying rectangle visible (useful for debug).

       --nowin
              Do not open any document windows.

       --version
              Display version information and exit.

       -h , --help
              Print option summary and exit.

REMOTE COMMANDS
       Since commands include parentheses, which have special meaning  to  the
       shell,  it  is  important  to  enclose  remote commands in quotes, like
       --remote &#8217;openURL()&#8217; so as to prevent the shell from  interpreting  the
       parentheses.   In the following, destination is one of new-window for a
       (new) background page (opened in an inactive new tab).

       openURL()
              Open "Go to" dialog box prompting for input.

       openURL(URL)
              Open URL in active window.

       openURL(URL,destination)
              open URL in destination window, tab or background.

       openFile(destination)
              Open file selector in destination window or page (background not
              supported).

       openM2(new-window)
              Open Opera mail client list view in a new window.

       openComposer(new-window)
              Open Opera mail composer in a new window.

       addBookmark(URL)
              Add URL to bookmark list.

       raise()
              Raises the Opera window.

       lower()
              Lowers the Opera window.

FILES AND DIRECTORIES
       /usr/bin/opera
              Standard installation location for Opera driver script;  config-
              ures environment and invokes the binary.

       /usr/lib/opera/
              Installation  directory  for Opera binaries, in version-specific
              sub-directories, with a separate plugins/ sub-directory for plu-
              gins.

       /usr/share/opera/
              Opera  shared resource directory.  Contains assorted data files.

       /etc/opera6rc
              Default settings for Opera configurations; may be overridden  by
              the opera6.ini in a user&#8217;s personal configuration directory.

       /etc/opera6rc.fixed
              System  settings  for Opera configurations; cannot be overridden
              by users.

       ~/.opera/
              The default personal configuration directory.

CONFIGURATION DIRECTORY
       Private data for each user is stored in a personal configuration direc-
       tory.   By  default this is ~/.opera/ but you can override this by set-
       ting OPERA_PERSONALDIR (for example in your login shell&#8217;s standard con-
       figuration file) to a location of your choosing; or by passing a chosen
       directory with the --personaldir command-line  option.   For  the  most
       part  it  is best to access the files in this directory via the prefer-
       ence and appearance dialogs - accessed either from the  Tools  menu  of
       the Opera user interface or via a keyboard shortcut: type Alt+P for the
       main preferences dialog, Shift+F12 for the appearance dialog or  simply
       F12  for  a  menu of the more commonly set basic preferences from each.
       (You can control Opera entirely from the  keyboard,  including  any  of
       these dialogs; to dismiss a dialog, use the Esc key.)

       Most  files  in the directory have names which express their functions.
       Many of them have backups saved in *.bak files.  The file opera6.ini in
       this  directory records most user preferences.  Entries in it can over-
       ride the locations of some of the other files; this description relates
       each  to its default location.  A fuller account of the opera6.ini file
       may  be  found  at   http://www.opera.com/support/usingopera/operaini/.
       Bookmarks  are  recorded  in opera6.adr, and global browsing history is
       recorded in global.dat; browsing histories for individual  tabs  are  a
       part  of  the  session state saved as files in sessions/.  In this sub-
       directory, the state of the current session is saved  in  autosave.win;
       other sessions may be saved (see the Sessions sub-menu of the main File
       menu) to other files in this directory.  It is prudent to save  such  a
       named  session  before  starting  up Opera with a radically new version
       (especially if it is a beta release).

ENVIRONMENT VARIABLES
       OPERA_PERSONALDIR Override default personal configuration directory

       OPERA_STRICT_FILE_PERMISSIONS Use owner-only permissions for all  files
       created  (as  if  by umask 077) if set to YES, TRUE (case insensitively
       matched) or 1.  Otherwise honour umask setting in the normal way.

AUTHOR
       This program was written by Opera Software  ASA  http://www.opera.com/.
       Please refer to /usr/share/doc/opera/LICENSE for more information.

BUG REPORTS
       If    you    find    a    bug    in   Opera   please   report   it   to
       https://bugs.opera.com/wizard/

SEE ALSO
       X(1)

       umask(1)

       Output from opera --help for a fuller list of supported options.

       http://www.opera.com/docs/switches/ for an on-line account of the  sup-
       ported options.

       http://help.opera.com/  for  more  general on-line help (also available
       via the Help menu on Opera&#8217;s main toolbar).

                                 February 2006                        OPERA(1)
(END) 

I pretty much knew all that information.  Is there any other way of getting more opera command for the terminal?

---

### Post by Sugi on 2007-12-17
Bump

---

