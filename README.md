# config

Personalized configuration for my macOS systems.

## Installation

### Brew

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

### Bundle

```sh
brew bundle
```

### zsh-autosuggestions

```sh
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.zsh/zsh-autosuggestions
```

### nvm

https://github.com/nvm-sh/nvm for updated install script, otherwise:

```sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.0/install.sh | bash
```

### Fonts

https://developer.apple.com/fonts

### Use Touch ID for sudo

Add the following line to `/etc/pam.d/sudo`:

```
auth       sufficient     pam_tid.so
```

The file should look something like:

```sh
# sudo: auth account password session
auth       sufficient     pam_tid.so
auth       sufficient     pam_smartcard.so
auth       required       pam_opendirectory.so
account    required       pam_permit.so
password   required       pam_deny.so
session    required       pam_permit.so
```

## Automator

### Update Config

#### Run Shell Script

```sh
export PATH=/usr/local/bin:$PATH

cd ~/Repos/config

# .zshrc
cat ~/.zshrc > .zshrc
git add .zshrc
git commit -m "Update .zshrc"

# Brewfile
brew bundle dump -f
git add Brewfile
git commit -m "Update Brewfile"

git push
```
