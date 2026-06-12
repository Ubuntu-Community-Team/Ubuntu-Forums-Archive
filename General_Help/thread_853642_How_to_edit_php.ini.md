---
title: "How to edit php.ini"
date: 2008-07-08
forum: General Help
---

### Post by Jimbo13 on 2008-07-08
I'm setting up a Jinzora media server it's been going fairly well thanks to this great tutorial [http://rubbervir.us/projects/ubuntu_media_server/part2.html](http://rubbervir.us/projects/ubuntu_media_server/part2.html).


Anyways, I'm stuck figuring out how to edit the php.ini


Instructions from the tutorial:
[B]
     Now that LAMP (Linux Apache MYSQL PHP) is installed we have to configure PHP 5 to meet the Jinzora2 requirements.

        sudo pico /etc/php5/apache2/php.ini

        Now set

            "max_execution_time" to 300
            "memory_limit" to 128M
            "post_max_size" to 32M
            "file_uploads" to On
            "upload_max_filesize" to 32M 
[/B]

I  put in :sudo pico /etc/php5/apache2/php.ini then pasted 
            "max_execution_time" to 300
            "memory_limit" to 128M
            "post_max_size" to 32M
            "file_uploads" to On
            "upload_max_filesize" to 32M 

Then ctrl+x to save, but that didn't seem to do it, so I how do set the values in the php.ini?


:guitar:

---

### Post by Master Chief on 2008-07-08
Look at the bottom of the screen: ctrl+o (write out) followed by ctrl+x

---

### Post by Jimbo13 on 2008-07-09
Thanks, yeah I found it.

The data I was looking for was scrolled off, I ended up editing it in the system.

---

### Post by comandrei on 2008-07-09
I don't think that will work.If you pasted the values at the beginning of the file, they will be overwritten by the defaults. Try to look through the file and change each value manually. Check with phpinfo() if your values were changed.

---

