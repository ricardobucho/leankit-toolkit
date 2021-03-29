# Leankit Toolkit (Kit)

This script was made to improve the speed of switching between cards as well as provide an overview to its user of what is in progress at any given time. A card must always be added to `kit` manually with the proper command and has to be moved between states manually as well. All operations are local, nothing is synchronized elsewhere.

## Requirements
* Kit was built using Ruby 2.5.7 and was not tested with older or newer versions, use at your own discretion

## Installing
* Clone this repo somewhere
* `cd` into it and run `bundle` to install all dependencies
* Duplicate `.env.example` to `.env` and fill in your info
* Add the `alias` below to your `.zshrc` file

## Environment Configuration
* `LEANKIT_ACCOUNT_NAME`: Whatever is before the `.leankit.com`
* `LEANKIT_USER_EMAIL`: Your email
* `LEANKIT_USER_PASSWORD`: Your password
* `GIT_INITIALS`: Your initials to be used when creating a branch
* `DEPLOY_BRANCH`: The branch name of which subsequent branches are to be created from

## Alias
* Make sure the directory within the alias matches your installation path

```bash
# Kit
kit() {
  CMD=$1
  CARD_ID=$2
  LANE=${3:-dev}
  QUIET=${4:-1}

  ~/leankit-toolkit/v1/kit --command=$CMD --lane=$LANE --id=$CARD_ID --quiet=$QUIET
}
```

## Common Commands
* Most if not all commands have a long and a short name
* Available lanes are: `dev`, `rev`, `fs`, `acc`, `mrg` and `arc`

```bash
# List all commands [help|h]
kit help

# Add a card from leankit [branch|b]
# This command switches to the deploy branch and creates a branch from there.
kit branch LK_CARD_ID

# Move a card to a different state [move-card|mc]
kit move-card xx0000 mrg

# List all imported cards without their description [list|l]
kit list

# List all imported cards with their description [review|r]
kit review
```

## Disclaimer
* Code is not high quality and any standard it might match is pure coincidence
* Feel free to let me know about any issues or features that would be cool to add
* A V2 is in the works which tries to make it a bit more readable and performant (no ETA)
