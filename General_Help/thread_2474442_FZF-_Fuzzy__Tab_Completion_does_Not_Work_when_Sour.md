---
title: "FZF- Fuzzy ** Tab Completion does Not Work when Sourcing from .bashrc"
date: 2022-04-29
forum: General Help
---

### Post by TJSL on 2022-04-29
FZF- Fuzzy ** Tab Completion does Not Work when Sourcing

        OS: Ubuntu 22.04
        fzf --version: 0.29 (devel)
        FZF: [https://github.com/junegunn/fzf](https://github.com/junegunn/fzf)


        TL;DR - Manually sourcing /usr/share/bash-completion/completions/fzf enables tab completion (cd **) to work
        (source /usr/share/bash-completion/completions/fzf). However, it does not work when sourcing from ~/.bashrc. (Technically, my .bashrc is just sourcing the files in ~/.bashrc.d/. This makes it easier to manage with ansible and is working fine with all my other .bashrc files).


        ~/.bashrc

        while read filename
        do
          source "$filename"
        done < <(find -L ~/.bashrc.d -type f)



        ~/.bashrc.d/.bashrc_fzf

        source /usr/share/bash-completion/completions/fzf 



FZF documentation (apt-cache show fzf) directs user to the following readme (/usr/share/doc/fzf/README.Debian) and provides the following instructions:

        Append this line to ~/.bashrc to enable fzf keybindings for Bash:

           source /usr/share/doc/fzf/examples/key-bindings.bash

        Append this line to ~/.bashrc to enable fuzzy auto-completion for Bash:

           source /usr/share/doc/fzf/examples/completion.bash
           

        It does not appear that the file /usr/share/doc/fzf/examples/completion.bash exists, but has been moved to /usr/share/bash-completion/completions/fzf (which identifies itself as FZF completion.bash in the file heading). Manually sourcing this file causes tab completion to work (source /usr/share/bash-completion/completions/fzf).

        Troubleshooting steps:
        Tested on a new Ubuntu installation
Sourcing /usr/share/bash-completion/completions/fzf enables tab completion works when it is manually sourced
        Root is the user and group for the /usr/share/bash-completion/completions/fzf file, but it has read permissions for owner/group/other.
        I placed a debug echo statement within ~/.bashrc.d/.bashrc_fzf to ensure that .bashrc is reading the file.
        see "Fuzzy completion not working #1119" ([https://github.com/junegunn/fzf/issues/1119)(solution:](https://github.com/junegunn/fzf/issues/1119)(solution:) explicit source file)
Considered possibility of later sourced file causing conflicts (do not believe this is the case, but am unsure how to fully test)
I tried sourcing /usr/share/bash-completion/completions/fzf directly from .bashrc (rather than ~/.bashrc.d/)

It is possible that this is related to the order in which .bashrc settings are loaded (see [https://github.com/junegunn/fzf/issues/872](https://github.com/junegunn/fzf/issues/872)).

---

### Post by TJSL on 2022-04-29
It appears that there was a conflict within the .bashrc files. Sourcing the fzf files last solved the problem.

---

