---
title: "Syntax error in Limewire bash script"
date: 2006-11-19
forum: General Help
---

### Post by tinker123 on 2006-11-19
Well, one day limewire worked, the next it did not.  When I try to run it, I get this error message:

runLime.sh: 44: Syntax error: "(" unexpected (expecting "}")


I tried looking the file,  a bash script, but I am not really educated in bash syntax.  I know the problem is probably right in front of my face, but I don't see where the syntax error is.  Here is the block of code from that script:

############
look_for_javaImpl() 
{
  IFS=$'\n'
  # the line below this is line 44
  potential_java_dirs=(`ls -d1 "$JAVADIR"/j* | sort | tac`)
  for D in "${potential_java_dirs[@]}"; do
    if [[ -d "$D" && -x "$D/bin/java" ]]; then
      JAVA_PROGRAM_DIR="$D/bin/"
      echo $MSG2 $JAVA_PROGRAM_DIR
      if check_version ; then
	return 0
      fi
    fi
  done
  echo $MSG8 "${JAVADIR}/" $MSG9 ; echo $MSG4
  return 1 
}


##############

Can anyone see where the brackets or parens are unbalanced?

Thanks

---

### Post by ThrobbingBrain66 on 2006-11-19
you have to edit the /usr/bin/limewire file.

the third(last) line starts with 'sh' and this needs to be changed to 'bash'

---

### Post by hal10000 on 2006-11-19
flame limewire, get azureus and you feel as if you are in paradise
(for azureus you may need sun-java5 runtime.

---

### Post by tinker123 on 2006-11-19
> **ThrobbingBrain66 said:**
> you have to edit the /usr/bin/limewire file.

the third(last) line starts with 'sh' and this needs to be changed to 'bash'


Thanks much!

---

