---
title: "different version of app in tmux window"
date: 2015-09-08
forum: General Help
---

### Post by matthew_smith2 on 2015-09-08
I have been pulling my hair out to figure this out.  I am trying to use the AWS CLI tools to run a command.  It works fine in a normal ssh window, but in my tmux window, it seems to be referencing the older version.  Can anyone help me fix this?

I upgraded to the latest version following the instructions by running these commands:

curl -O [https://bootstrap.pypa.io/get-pip.py](https://bootstrap.pypa.io/get-pip.py)

sudo python get-pip.py

sudo pip install --upgrade awscli

When I run(in the main ssh window):
aws --version
I get:
aws-cli/1.8.2 Python/2.7.6 Linux/3.13.0-51-generic

But within the tmux window, I get this:
$ aws --version
aws-cli/1.2.9 Python/3.4.0 Linux/3.13.0-51-generic


Why isn't it seeing the latest version?  How can I fix this?  I am trying to run "aws ec2 describe-spot-fleet-requests" in a shell script invoked from the tmux window.

 Thank you.

---

