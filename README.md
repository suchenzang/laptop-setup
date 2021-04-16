# laptop-setup

## Keyboard/Trackpad stuff
* Keyboard repeat:
  ```
  defaults write -g InitialKeyRepeat -int 10 # normal minimum is 15 (225 ms)
  defaults write -g KeyRepeat -int 1 # normal minimum is 2 (30 ms)
  ```

* Use cmd-Q to invert colors:
  * Keyboard -> Shortcuts -> Accessibility -> Invert Colors

* Download BetterTouchTool
  * cmd + option + arrows = windows resizing max
  * cmd + shift + M = max window

## Color stuff
* Iterm2 color installation:
  * Load `suchenzang.itermcolors`
  * Open iTerm2′s preferences and go to Profiles -> Colors. 
    * Make sure that the minimum contrast slider is set to low
    * Click on text, make sure that “Draw bold text in bright colours” is disabled

* Modify `~/.bash_profile`:
  ```
  export PS1='\[\e[0;32m\]\u\[\e[m\]\[\e[1;32m\]>\[\e[m\] '
  alias ls='ls -G'
  ```
  * Or `~/.zshrc`:
  ```
  PROMPT='%(?.%F{46}√.%F{red}?%?)%f %B%F{14}%1~%f%b %# '
  alias ls='ls -G'
  ```

* Install f.lux

## Brew
* Install brew:
  ```
  ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
  ```

## Vim
* `nerdtree` and `pathogen`:
  ```
  mkdir -p ~/.vim/autoload ~/.vim/bundle;
  curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim
  cd ~/.vim/bundle
  git clone https://github.com/scrooloose/nerdtree.git
  vim ~/.vimrc
  ```

  Put this in `.vimrc`:
  ```
  execute pathogen#infect()
  call pathogen#helptags()
  syntax on
  filetype plugin indent on
  au VimEnter *  NERDTree
  set expandtab
  set tabstop=4
  set shiftwidth=4
  set number
  syntax enable
  ```

* To get syntax highlighting in vim for scala:
  ```
  brew install wget
  mkdir -p ~/.vim/{ftdetect,indent,syntax} && for d in ftdetect indent syntax ; do wget -O ~/.vim/$d/scala.vim https://raw.githubusercontent.com/derekwyatt/vim-scala/master/$d/scala.vim; done
  ```

## Miscellaneous
```
brew install tmux
brew cask install java
brew install scala --with-docs
brew install sbt
```

## Github
* Generate SSH keys and add to github:
  ```
  ssh-keygen -t rsa -b 4096 -C "suchenzang@gmail.com"
  ```
* Add to orgs, and switch notifications to work email.
