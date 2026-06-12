---
title: "Checkgmail not working"
date: 2007-08-08
forum: General Help
---

### Post by profediego on 2007-08-08
Hi everyone, 

I am trying to run checkgmail app, but it gives me this error 

Can't use an undefined value as a HASH reference at /usr/bin/checkgmail line 3691.
A thread exited while 2 threads were running.

So i go to that file in that line and i find this function, line 3691 is the last one.

sub set_language {
        my $xmlin = XMLin($translations, ForceArray => 1);

        ## For debugging ...
        # use Data::Dumper;
        # print Dumper $xmlin;

         %trans = %{$xmlin->{Language}->{$language}};
}


but i dont know what to do, can somebody tell me what happen, or how do i fix this please. 

Than ks...

---

### Post by apetresc on 2007-08-08
What language did you set in the Preferences pane for checkgmail?
At the moment, checkgmail doesn't work with any language that has 'special' characters, like French or German. You should remove the .checkgmail folder in your home directory, restart the program, and leave the language setting as "English".

---

### Post by profediego on 2007-08-08
Thanks that solved my problem.... ahhh why could i think of that... :p  Thank you very much!!!

---

