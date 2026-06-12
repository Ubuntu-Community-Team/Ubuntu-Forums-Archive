---
title: "spotify --help"
date: 2018-02-22
forum: General Help
---

### Post by andysharpie on 2018-02-22
So, every time I enter spotify --help, I get this at the top of the output list.
[FONT=courier new]
$ spotify --help
ln: failed to create symbolic link '/home/andy/snap/spotify/5/.config/gtk-2.0/gtkfilechooser.ini': File exists

W[FONT=arial]hat does this mean?[/FONT]
[/FONT]
Andy

---

### Post by Frogs Hair on 2018-02-22
I see the following though Spotify was installed via snap . Did you install the same way?

```


spotify --help
Usage: Spotify <options>
Options which take arguments must be given in the form --option=argument. Supported options include:




>
    Use as root for the cache directory.


--force-unicast-discovery
    Disable Spotify Connect discovery mDNS multicast receiving (N/A for macOS).


--help
    Show publicly available flags.


--log-file=<path>
    Save log output to file.


--minimized
    Start the app with the window minimized. Only works on Windows.


--mu=<value>
    Start with a special cache directory. Allows you to run multiple clients at the same time. Value can be anything (will be used as part of the cache name).


--password=<password>
    Use to automatically sign in on startup. Use together with `--username`.


--show-console
    Show more log output.


--trace-file=<path>
    Save a trace file to this path.


--uri=<uri>
    Start the client normally, but automatically navigate to the URI when initialized.


--url=<url>
    Start the client with the specified URL.


--username=<username>
    Use to automatically sign in on startup. Use together with `--password`.


--version
    Output the version of the app.



```

---

### Post by andysharpie on 2018-02-22
I installed it using the Ubuntu Software application, not the terminal, if that helps any.

---

### Post by Frogs Hair on 2018-02-22
> [COLOR=#000000][FONT=&quot]/home/andy/**snap**/spotify/5[/FONT][/COLOR] It is a snap pkg.  Do you see the rest of the options regardless of the error ?

---

### Post by andysharpie on 2018-02-22
Yes, the rest of the options appear after that. What is a symbolic link, though?

---

### Post by Frogs Hair on 2018-02-23
> **andysharpie said:**
> Yes, the rest of the options appear after that. What is a symbolic link, though?

 
Symbolic links: Refer to a symbolic path indicating the abstract location of another file . I find only two posts so far on this error relating to snap and neither explains the cause very well.

---

### Post by andysharpie on 2018-02-23
So, if the file exists to which the simlink is trying to link, then why is it even a problem in the first place? Or do I not fully understand the "ln" message?

---

### Post by Frogs Hair on 2018-02-23
Run the following in the terminal . As for the warning I wouldn't be overly concerned about it.    
 ```
ln --help
```

---

### Post by andysharpie on 2018-02-23
Ok, thanks.

---

