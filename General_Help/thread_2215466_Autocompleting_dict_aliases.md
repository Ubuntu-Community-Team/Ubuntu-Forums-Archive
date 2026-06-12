---
title: "Autocompleting dict aliases"
date: 2014-04-06
forum: General Help
---

### Post by AmateurDev on 2014-04-06
Hello all,

I have a few aliases set up for dict corresponding to which dictionaries I would like to use:
```
alias define='dict -d gcide'
alias engfr='dict -d fd-eng-fra'
alias freng='dict -d fd-fra-eng'
alias thsrus='dict -d moby-thesaurus'
```

I'd like to be able to autocomplete the words that I search as if I typed out the actual commands. I used code based on [this forum post]("http://ubuntuforums.org/showthread.php?t=733397") on autocompleting bash aliases. I am just testing the define function right now; here's a copy of my .bash_aliases file:
```
alias define='dict -d gcide'
source /usr/share/bash-completion/completions/dict
# make-completion-wrapper _dict _definition dict -d gcide
function _definition {
    ((COMP_CWORD+=2))
    COMP_WORDS=( dict -d gcide ${COMP_WORDS[@]:1} )
    _dict
    return 0
}

complete -o default -F _definition define
```

However, when I try to autocomplete the word, the complete function strips the last argument to the last letter. For instance,
```
$ define fa<tab>
```
changes to
```
$ define a
```

Using a one-letter argument works correctly, but returns 3,000+ words which is unhelpful. Can anyone shed some light on how to make this function not delete the last characters?

Thanks!

---

