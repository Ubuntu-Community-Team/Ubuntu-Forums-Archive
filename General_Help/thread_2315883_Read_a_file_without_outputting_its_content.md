---
title: "Read a file without outputting its content"
date: 2016-03-03
forum: General Help
---

### Post by Drenriza on 2016-03-03
Hi all

I am wondering, how can you read the content of a file while suppressing its output to the screen but piping stdout to ssh.

When i do the below command it all gets very slow because zcat output everything it reads to the screen which slows down the entire process
  due to the fact that (from what i know) zcat writes to and clear the buffers over and over.
```
/bin/zcat file.sql.gz | /usr/bin/ssh -v user@ip "${SSH_COMMAND}"
```

The ssh command content is as follows (compliment to above)
```

IFS='' read -r -d '' SSH_COMMAND <<'EOT'
        /bin/echo "connected to $( /bin/uname -a )"
        /usr/bin/sudo /usr/bin/tee -a /mnt/file.sql.gz 
EOT

```

I have tried messing around with the redirect symbols before the pipe to try and redirect stdout into the pipe (just a thought), but i end up discarding stdout entirely which is then never piped to ssh.

Hoping someone can point me in the right direction.

Thanks in advance
Kind regards

---

### Post by nerdtron on 2016-03-03
Can you elaborate more on what are you trying to achieve here? Maybe we can offer other solutions.

From the looks of it, you use the tee command which will surely output to stdout, instead why not another redirection on that? 


And are you trying to send an sqldump and import it to another host? Why not try to directly import it to the remote host?

```
 gzip -c database.gz | mysql -uroot -p database_name -h mysql.server.IP 
```

---

### Post by Drenriza on 2016-03-03
> **nerdtron said:**
> Can you elaborate more on what are you trying to achieve here? Maybe we can offer other solutions.

From the looks of it, you use the tee command which will surely output to stdout, instead why not another redirection on that? 


And are you trying to send an sqldump and import it to another host? Why not try to directly import it to the remote host?

```
 gzip -c database.gz | mysql -uroot -p database_name -h mysql.server.IP 
```

Thanks for your reply nerdtron.

I have updated #0
The goal is that i wanted to see if /usr/bin/tee -a would keep the file integrity when doing a mysql dump compressed with gzip -c, like cat >> does just moving data from A to B.

And i dont have a test DB i can play with, dumping from and see if it works.

---

### Post by Drenriza on 2016-03-03
Sorry for the question guys, i found a test db which i can use to make the dump and run it through tee -a.
So i can do the dump directly and not read it from a already dumped file.

So it all solved itself:KS

---

