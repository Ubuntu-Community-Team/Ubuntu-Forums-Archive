---
title: "Correct syntax for this script?"
date: 2017-01-26
forum: General Help
---

### Post by AwaitingUserInput on 2017-01-26
I want to add the Brave web browser to my kubuntu 16.04 machine. On the Brave site they give instructions for adding their repository and the associated keys, but I get errors. The code they give is long and there's a line break. I think my problems are coming from putting the space in the wrong spot during the "apt-key add" portion. Can anyone proofread this or format it so that I can cut & paste?

From [this site]("https://github.com/brave/browser-laptop/blob/master/docs/linuxInstall.md"), right at the top:

```

curl https://s3-us-west-2.amazonaws.com/brave-apt/keys.asc | sudo apt-key add -
echo "deb [arch=amd64] https://s3-us-west-2.amazonaws.com/brave-apt `lsb_release -sc` main" | sudo tee -a /etc/apt/sources.list
```

---

### Post by efflandt on 2017-01-26
It looks like you are listing exactly what they list. It may help to also copy paste the actual error you get (in code tags).

---

### Post by AwaitingUserInput on 2017-01-26
Here is what I typed and what resulted in the terminal:

```
$ curl [https://s3-us-west-2.amazonaws.com/brave-apt/keys.asc](https://s3-us-west-2.amazonaws.com/brave-apt/keys.asc) | sudo apt-key add -echo "deb [arch=amd64] [https://s3-us-west-2.amazonaws.com/brave-apt](https://s3-us-west-2.amazonaws.com/brave-apt) `lsb_release -sc` main" | sudo tee -a /etc/apt/sources.list
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0gpg: conflicting commands
100  3165  100  3165    0     0   3334      0 --:--:-- --:--:-- --:--:--  3331
(23) Failed writing body
```

---

### Post by deadflowr on 2017-01-26
Those are two different commands
first run the curl >> sudo apt-key add -   command as is.
then run the echo command
not together.

---

### Post by Habitual on 2017-01-26
> **AwaitingUserInput said:**
> Here is what I typed and what resulted in the terminal:

```
$ curl [https://s3-us-west-2.amazonaws.com/brave-apt/keys.asc](https://s3-us-west-2.amazonaws.com/brave-apt/keys.asc) | sudo apt-key add -echo "deb [arch=amd64] [https://s3-us-west-2.amazonaws.com/brave-apt](https://s3-us-west-2.amazonaws.com/brave-apt) `lsb_release -sc` main" | sudo tee -a /etc/apt/sources.list
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0gpg: conflicting commands
100  3165  100  3165    0     0   3334      0 --:--:-- --:--:-- --:--:--  3331
(23) Failed writing body
```

Try  
```
sudo wget -q [https://s3-us-west-2.amazonaws.com/brave-apt/keys.asc](https://s3-us-west-2.amazonaws.com/brave-apt/keys.asc) -O- | sudo apt-key add -
```
for the key stuff.

---

### Post by AwaitingUserInput on 2017-01-26
> **deadflowr said:**
> Those are two different commands
first run the curl >> sudo apt-key add -   command as is.
then run the echo command
not together.

Ah! You are correct! I thought that their instruction webpage was wrapping the text at an inconvenient spot. It would have been nice if they used a $ to indicate a new terminal prompt.

Thank you. Everything worked correctly. I'm marking the thread as solved.

---

