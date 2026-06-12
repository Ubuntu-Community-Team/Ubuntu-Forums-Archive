---
title: "wget | How to automatically launch script and pass parameters to the script?"
date: 2020-04-04
forum: General Help
---

### Post by suaro on 2020-04-04
Hi Everyone,

I hope I'm posting to the correct forum section and apologize in advance if I've placed this in the wrong area :(

I have a python script called python1.py which is hosted on a remote web server. 

I'm able to successfully download and execute the python script (from bash script)  using wget such as below: 

       ```
wget -O - https://<server>/public/python1.py | python 
```

Everything works fine and there's no problem.   Now,  I need to modify the python1.py to receive a parameter. 

Testing the python1.py script (outside of the wget download/execution )  using something like this:

      ```
python python1.py 11m 
```

   ....works fine.   The python1.py app successfully reads the parameter (11m) and handles accordingly. 

**My question:**

  How can I pass the python parameter using the wget download/execute technique above?  I've tried a few variations, but none seem to work:

        **Attempt 1:**

        ```
wget -O - https://<server>/public/python1.py | python $1  
```

        This fails with :  python: can't open file '11m'  - which makes sense.  Python is looking for a file called 11m. 


         **Attempt 2:**

         ```
wget -O - https://<server>/public/python1.py **"**$1**"** | python   
```

         This fails with : 
```
[INDENT=2]2020-04-04 08:49:36 (67.8 MB/s) - written to stdout [2857/2857][/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]--2020-04-04 08:49:36--  http://11m/[/INDENT]
[INDENT=2]Resolving 11m (11m)... failed: Name or service not known.[/INDENT]
[INDENT=2]wget: unable to resolve host address ‘11m’    <<  wget seems to interpret as host address[/INDENT]

```     

          **Attempt 3:** (quotes removed - but essentially same as previous failure)

          ```
wget -O - https://<server>/public/python1.py $1 | python   
```


```
[INDENT=2]2020-04-04 08:52:14 (349 MB/s) - written to stdout [2857/2857][/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]--2020-04-04 08:52:14--  http://11m/[/INDENT]
[INDENT=2]Resolving 11m (11m)... failed: Name or service not known.[/INDENT]
[INDENT=2]wget: unable to resolve host address ‘11m’[/INDENT]

```
I can work around the problem by breaking up the download and execution of the python file into two different steps
  but would like to find out what I'm doing wrong and do everything in one step. 

Does anybody have any idea how to pass a parameter ?

Any tips / suggestions greatly appreciated as always. 

Thanks so much

---

### Post by lvm on 2020-04-04
If you want python to take arguments for a script read from stdin you should use - as the name of the file, in your case "wget -O - https://<server>/public/python1.py | python - 11m"

---

### Post by suaro on 2020-04-04
Thanks so much lvm.    That did the trick!

---

