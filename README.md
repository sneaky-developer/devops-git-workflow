# Creating github repository manually and adding app.js manually

# From cli creating new branch feature

# Merging feature branch with main branch

# Intergrating pre-hook by adding file in .git/hooks/pre-commit
it have these lines of code
#!/bin/sh
#This script enforces rules for the pre-commit hook.
#Check for trailing whitespace
if git diff --check --cached | grep -E '^\+.*\s$'
then
    echo "Error: Trailing whitespace detected. Please remove."
    exit 1
fi

#Check for debugging statements
if git diff --cached --name-only | grep -E '\.(js|ts)$' | xargs grep -E 'console\.log|debugger'
then
    echo "Error: Debugging statements detected. Please remove."
    exit 1
fi
#If everything is okay, allow the commit to proceed
exit 0


# Integrating post-hook by adding file in .git/hooks/post-commit
it have these lines of code
#!/bin/bash
SLACK_WEBHOOK_URL="https://app.whistleit.io/api/webhooks/64d1f8fc602e1e5d893bc831"
#Send congratulatory message
curl -X POST -H 'Content-type: application/json' --data '{"text":"Post commit is succes by: ALi Mehdi"}' $SLACK_WEBHOOK_URL

# when i commit with app.log("hello") and empty spaces on the end of line
![image](https://github.com/sneaky-developer/devops-git-workflow/assets/72550706/d8fb1f0b-86a6-4577-bb1d-675256341a6b)

# when any push or pull occurs it gives message to the channel
![image](https://github.com/sneaky-developer/devops-git-workflow/assets/72550706/55662611-270c-420c-a93c-7aaa40ef371f)
