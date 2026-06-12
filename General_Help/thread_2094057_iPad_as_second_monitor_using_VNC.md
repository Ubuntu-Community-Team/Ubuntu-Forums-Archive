---
title: "iPad as second monitor using VNC"
date: 2012-12-12
forum: General Help
---

### Post by Madrid1978 on 2012-12-12
Hi all, I'm trying to use my iPad as a second monitor in Ubuntu 12.10.

Now I can use VNC in the iPad to connect to my box, but I just see a copy of my current workspace (workspace 1). 

What I would like to do is configure the VNC server so that it sends to the iPad the contents of workspace 2. That way I could send any window to workspace 2 and see it on the iPad while in my computer screen I see workspace 1. 

Do you know if this is possible? In the vino preferences windows there's no way of choosing the workspace. Maybe I should use some other VNC server that allows this? Is there another way of doing what I want?

Thanks in advance! :)

---

### Post by Madrid1978 on 2013-01-05
I haven't found a way to do what I wanted, so I'm using a workaround, it's dirty but it works:

Since I have an Apache server in my box, I just configured the gnome-screenshot program to save the screenshot files in my htdocs folder. A simple PHP script reads the screenshot file and serves it as a png. In the iPad I open Safari and point to that PHP script.

When I want to send a window to the iPad I just press the PrintScreen and in five seconds (the PHP file refreshes the image every five seconds) I see it in the iPad. Of course, what I get on the iPad it's just an image, not the real thing, but I can use it to display documents, db tables, that kind of things.

[IMG]http://i.imgur.com/pxa9X.jpg?1[/IMG]

Here is the PHP script:

```

<?php
if ($_REQUEST['get'])
{
    header('Content-type: image/png');
    $d = dir(".");
    while (false !== ($entry = $d->read())) 
    {
        if (strpos($entry, 'shot') > -1)
           {    
               unlink('lastCapture.png');
               rename($entry, 'lastCapture.png');
           }
    }
    $d->close();
    readfile('lastCapture.png');
    die();
}
?><!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="initial-scale=1.0; maximum-scale=1.0; user-scalable=0;" />
        <meta name="apple-mobile-web-app-capable" content="yes" />
    </head>
    <body style='background:#000'>
        <img id='im' src='http://192.168.0.199/tmp/desktop.php?get=1' onclick="this.src='http://192.168.0.199/tmp/desktop.php?get=1'"/>
    </body>
    <script>
    function refreshImg()
    {
        document.getElementById('im').src='http://192.168.0.199/tmp/desktop.php?get=1';
    }
    setInterval(refreshImg, 5000);
    </script>
</html>

```

---

