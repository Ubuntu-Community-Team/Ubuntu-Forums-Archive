---
title: "Problem with ssh and github (diagnostics work but push doesn't)"
date: 2021-08-20
forum: General Help
---

### Post by southof40 on 2021-08-20
I have problems using ssh to conduct git operations on github and I'd be grateful if someone could suggest what I might be doing wrong.

Specifically I'm having problems doing a push to a newly created repository


It's worth mentioning that the key that I have uploaded to Github for use with my account  has a non-standard name (I'll call it '**id_ed25519_ABCDEFGHI**'), I mention this because a lot of directions  assume that you have a default name.

Also when you see the email address '**foo@not_the_actual_domain_used.com**'  below that is the email address which Github associates with me.

In case it matters I have multiple keys in ~/.ssh and I have multiple keys uploaded to my Github account. All private key files have permissions of 600 , all public key files have permissions of 644 .

I have just created a new repos within the Github UI called 'my-test-repos' and I'm now attempting to push to it.



I go through the following sequence ...

```
foo@bar:~/src/my-test-repo$ cat /home/foo/.ssh/id_ed25519_ABCDEFGHI.pub
ssh-ed25519 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA [EMAIL="foo@not_the_actual_domain_used.com"]foo@not_the_actual_domain_used.com[/EMAIL]

foo@bar:~/src/my-test-repo$ ssh-add -l
The agent has no identities.

foo@bar:~/src/my-test-repo$ ssh-add  /home/foo/.ssh/id_ed25519_ABCDEFGHI
Identity added: /home/foo/.ssh/id_ed25519_ABCDEFGHI (foo@not_the_actual_domain_used.com)

foo@bar:~/src/my-test-repo$ ssh-add -l
256 SHA256:BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB [EMAIL="foo@not_the_actual_domain_used.com"]foo@not_the_actual_domain_used.com[/EMAIL] (ED25519)

foo@bar:~/src/my-test-repos$ git config --add --local core.sshCommand 'ssh -i /home/foo/.ssh/id_ed25519_ABCDEFGHI'

foo@bar:~/src/my-test-repo$ git push -u origin main
Username for 'https://github.com': 

```

As you can see when I do a `git push` I get prompted for a username (and a password if I supply a username). I would like the authentication to be done with key exchange.

In the output shown above to the `ssh-add -l` command the 'BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB' matches what I see for one of the keys visible when I go to the settings of my github account.


If I do this (one of the standard suggested diagnostics) I get this successful exchange ...


```
foo@bar:~/src/my-test-repo$ ssh -T [EMAIL="git@github.com"]git@github.com[/EMAIL]
Hi my_github_username! You've successfully authenticated, but GitHub does not provide shell access.
```

also 

```
foo@bar:~/src/my-test-repo$ ssh -i /home/foo/.ssh/id_ed25519_ABCDEFGHI -T [EMAIL="git@github.com"]git@github.com[/EMAIL]
Hi my_github_username! You've successfully authenticated, but GitHub does not provide shell access.
```


I'd be grateful if anyone could suggest some other diagnostics I could try to analyse what the problem is with the `push` operation is .


Thanks.

---

### Post by TheFu on 2021-08-20
Have you setup a ~/.ssh/config file with the identity file specified for the different git repos?  Every ssh-using tool I know honors that file.

The manpage for it is ssh_config ... but if you put it in your ~/.ssh/ it will be used just for your system.

Also, ~/.ssh/ should be 700. But I'm guessing that permissions are fine if the ssh tests are working.

Do you have a copy of **Pro Git**?  Should be a free PDF and should answer this question.  I've only used it a few times - it had the answer and worked quickly.  I don't use github (won't have an account on that service since the take-over), but with my own repos, different identity files work fine.

---

### Post by southof40 on 2021-08-21
Thanks @TheFu , I won't have time to try this tonight but I just wanted to acknowledge your suggestion. I will try it soon and reply back to the thread. Thanks again.

---

### Post by southof40 on 2021-08-22
OK the problem was indeed related to the ~/.ssh/config . Another issue I had was that the repos I was testing this against had been cloned via https and not ssh. Github no longer allows that to be used and just prompts for a uid/pwd when it encounters it. Anyway changing the remotes for that repository then allowed everything to work. Thanks very much for your suggestion.

Funny thing about 'Pro Git', I do indeed have a copy and it's sitting within arms length of my desk but I find increasingly I forget to look at books instead spending far too long searching the web. This isn't the first time I've failed to consult a book which might have been much more effective than lots of surfing.

Thanks again.

---

### Post by TheFu on 2021-08-22
I have a PDF version of Pro Git in my Calibre library. I'll usually spend 3-5 minutes looking online and if that doesn't work, will flip through my library for answers.  Obviously, I have to know which sort of references are in the library.  

I do Ruby and Perl and C/C++.  Lots of books on those at all levels for almost any problem.

Simple Linux Admin stuff is what my library has, which isn't often useful, since it is all 5-25 yrs old.

For ssh stuff, it is mostly learned experience, though I've thumbed through the O'Reilly book on ssh at book stores.  The ssh_config and sshd_config file manpages are pretty clear, but if someone doesn't have any idea about the capabilities, that makes it hard to know.  ssh is freakin' amazing. Too bad only Unix-people really understand the power.   Same for rsync.  Those two tools are the basis for so many other tools we use all the time.

---

