---
title: "help with LIRC with internal IR transceiver NP5790"
date: 2008-05-19
forum: General Help
---

### Post by yogithebear73 on 2008-05-19
Hi, I've got a Sager NP5790 with an internal IR transceiver here's a link to specs: [http://www.powernotebooks.com/specs/Sager/5790specs.php]("http://www.powernotebooks.com/specs/Sager/5790specs.php")

running a fresh install of hardy.

There is also an internal TV-tuner card that came with a remote, likely making the internal IR transceiver bundled hardware with the TV-tuner card.
The model is: Yuan MPC788. 

It also came with a card sized 26 button remote, Vista MCE IR remote controller: RC115V link:[http://www.edio21.com/prod_rc115v.asp#]("http://www.edio21.com/prod_rc115v.asp#")

I've spent the better part of 4 hours searching for a way to make LIRC work with my system. I have failed. I used synaptic to install lirc and choose various combinations of remotes and transmitters when my initial guesses were incorrect.

After guessing about hardware, i did irw to see if I could get a response. Either the terminal returned empty prompting me to do a second input of irw resulting in a refused connection, or the terminal hung waiting for ir input, which never arrived i.e. pressing buttons did nothing.

I do not even know if I have a transmitter; the description for a transmitter was an IR sender and receiver, which makes me wonder what a transceiver is, because that sounds like a transmitter and receiver melded into a single word. Is an IR transmitter the same thing as an IR transceiver? 

I've tried all the instructions on this website: [https://help.ubuntu.com/community/InstallLirc/Hardy]("https://help.ubuntu.com/community/InstallLirc/Hardy")
please do not simply direct me there.

The above website's instructions for recording a remote also did not work.

Any ideas about what to do?

---

