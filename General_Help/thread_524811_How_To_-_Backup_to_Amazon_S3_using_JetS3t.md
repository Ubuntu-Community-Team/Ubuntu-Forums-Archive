---
title: "How To - Backup to Amazon S3 using JetS3t"
date: 2007-08-13
forum: General Help
---

### Post by DugieHowsa on 2007-08-13
I love my new digital camera.  It does both still photos and movies.  A side effect of this is that I now have a ton of data, and I would have a mental episode if I were to lose it.

Back when I was running Windows, I utilized a utility call [S3 Backup]("http://www.maluke.com/s3man/").  It was a very clean, simple way to back up my data to the [Amazon Simple Storage Service]("http://www.amazon.com/s3"), or S3 for short.  The Amazon S3 provides a very inexpensive and extremely flexible means of storing data.  Pricing details can be found [here]("http://www.amazon.com/s3").

But as the S3 Backup utility did not have a Linux port, I was still looking with a good alternative to use with Ubuntu.  Thats when I came across [JetS3t]("http://jets3t.s3.amazonaws.com/").  JetS3t is a free, open-source Java toolkit and application suite for the Amazon Simple Storage Service.

Using the synchronize utility, I can schedule backups to Amazon.  Here is how I went about setting it up.

1)  Download the JetS3t toolkit from here:
  [https://jets3t.dev.java.net/releases/jets3t-0.5.0.zip](https://jets3t.dev.java.net/releases/jets3t-0.5.0.zip)

2)  Create a directory called jetS3t in the /opt directory:
```
sudo mkdir /opt/jets3t
```

3)  Unzip the contents into the /opt directory:
```
unzip jets3t-0.5.0.zip -d /opt/jets3t
```

4)  Make the shell scripts in the bin directory executable:
```
chmod 755 /opt/jets3t/bin/cockpit.sh
chmod 755 /opt/jets3t/bin/synchronize.sh
chmod 755 /opt/jets3t/bin/uploader.sh
```

5)  Set the JETS3T_HOME environment variable:
```
export JETS3T_HOME=/opt/jets3t
```

NOTE:  To have this done automatically at startup, add the above line to the end of the ~/.bashrc file.
```
gedit ~/.bashrc
```

6)  Add your Amazon S3 Credentials to the /opt/jets3t/config/synchronize.properties file
```
  sudo gedit  synchronize.properties
```

7)  Run the synchronize script.  In the following example, I am UPloading the contents of the /media/server1/HomeMovies/ to the HomeMovies Bucket:

```
/opt/jets3t/bin/synchronize.sh UP HomeMovies /media/server1/HomeMovies/
```

8)  Use the cockpit utility to confirm the data is residing on the Amazon S3 server.
```
/opt/jets3t/bin/cockpit.sh
```

For full documentation on the Jet Toolkit, click the link below:
  [http://jets3t.s3.amazonaws.com/toolkit/configuration.html](http://jets3t.s3.amazonaws.com/toolkit/configuration.html)

---

### Post by davidme on 2007-09-16
Excellent post. I am confused about one thing, what does this whole thing mean and does?

Set the JETS3T_HOME environment variable:
Code:

export JETS3T_HOME=/opt/jets3t

NOTE: To have this done automatically at startup, add the above line to the end of the ~/.bashrc file.
Code:

gedit ~/.bashrc"

---

### Post by DugieHowsa on 2007-09-26
The JetS3t application uses an environmental variable called JETS3T_HOME in order to run.  Without setting this environmental variable, you will see errors when trying to run the application.  This sets the JETS3T_HOME variable to where the application has been installed.  The 2nd step automates the setting of this process so a user does not have to manually configure the variable every time the user logs on.

I hope this answers your question.

---

### Post by sandos on 2008-01-20
A ubuntu package for jets3t would be awesome! Anyone? ;)

---

### Post by DugieHowsa on 2008-02-16
Just wanted to let every one know that the next stable version of JetS3t, version 0.6, was released in February 2008.

[http://jets3t.s3.amazonaws.com/downloads.html](http://jets3t.s3.amazonaws.com/downloads.html)

---

