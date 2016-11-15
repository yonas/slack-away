# slack-away

Slack-Away is a Bash script that automatically sets your active/away status in [Slack](https://slack.com).

By default, Slack-Away will set your status to Away on Slack if you are idle (no mouse or keyboard activity) for 10 minutes or more. Otherwise, you will be set to Active.

## Requirements

- Bash (`apt-get install bash`)
- Curl (`apt-get install curl`)
- xprintidle (`apt-get install xprintidle`)

## Installation

1. Install dependencies.
    ```
    apt-get install bash
    apt-get install curl
    apt-get install xprintidle
    ```

2. Clone this repository.

    ```
    git clone git@github.com:yonas/slack-away.git
    cd slack-away
    ```

3. Create a Slack test token at https://api.slack.com/docs/oauth-test-tokens

4. Edit the `slack-away-bot` file.
 * a) [required] Replace `<SLACK_TOKEN_HERE>` with your Slack test token from step 2.
 * b) [optional] Edit the `idle_timeout_minutes` variable to change the idle timeout. The default is 10 minutes.

5. Mark the files as executable.

    ```
    chmod 755 slack-away-bot
    chmod 755 slack-away-launcher
    ```

6. Setup cron to run `slack-away-launcher` every minute.
    
    Run the crontab editor:
    ```
    crontab -e
    ```
    and add the following:

    `    *        *          *             *                *               /path/to/slack-away/slack-away-launcher > /dev/null 2>&1`

    Make sure to replace `/path/to/slack-away` with the actual path to where you cloned `slack-away` in step 1.
