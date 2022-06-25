# Display current git branch name in terminal or VS code
step 1: create a file as .zshrc in Users/your_name/ directory and open it using TextEditor
(note: no need to create if already exist)

step 2: paste the below code at the end of that file and save it
```
function git_branch_name()
{
  branch=$(git symbolic-ref HEAD 2> /dev/null | awk 'BEGIN{FS="/"} {print $NF}')
  if [[ $branch == "" ]];
  then
    :
  else
    echo ' %F{cyan}('$branch')%f'
  fi
}

setopt prompt_subst;

PS1="%K{default}%F{magenta}%B%1~%b%f"'$(git_branch_name)'"%k %# "
```
step 3: restart your terminal to see the changes

![Screenshot 2022-06-25 at 9 53 30 AM](https://user-images.githubusercontent.com/55612421/175757866-13c34166-2c1c-4be6-8037-550ad248d258.png)

## To customise the style
Refer to this [zsh site](https://zsh.sourceforge.io/Doc/Release/Prompt-Expansion.html#Visual-effects) and change the PS1 value according to your choice
