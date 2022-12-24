
## Step 0:

Please refer to the [SETUP.md](./SETUP.md) file.

also to run your bot its easy you just need to commit and push your code and pls dont change the name of the file

## Step 1 -set up bot:

### 📑 **Description**:

in this step wee gonna make the your main file for the bot.
in this fie wee are gonna make the basique connection and make the bot say "hello word" in a chanel

to run a bot wee are gonna use discord library in that [lib](https://discordpy.readthedocs.io/en/latest/index.html) there a lots of things wee are not gonna use all to connect you only gonna need [Client](https://discordpy.readthedocs.io/en/latest/api.html?#discord.Client) and [run](https://discordpy.readthedocs.io/en/latest/api.html?#discord.Client.run) it that easy.

wee also gonna use [client.event](https://discordpy.readthedocs.io/en/latest/api.html?#discord.Client.event) to manage whats happening

```py
client = discord.Client()

@client.event
async def on_ready():
    print("i'm READY!!!")

client.run("BOTS TOKEN") //if you dont have it check task 0
```

there also a [message](https://discordpy.readthedocs.io/en/latest/api.html?#message) object where wee gonna find every thing from where is getting post to who send it but for the moment wee are gonna use the message.content to see whats is the message send

```py
client = discord.Client()

@client.event
async def on_message(message):
    print(message.content)

client.run("BOTS TOKEN") //if you dont have it check task 0
```

### 📌 **Tasks**:

    - create a bot.py
    - in that file create a on_ready event that print like in the example
    - in that file create a on_message event that print the message content

<details> 
<summary>✔️ Result preview</summary>
<p>import discord
import asyncio

client = discord.Client()

@client.event
async def on_ready():
    print("Capitaine Salamèche à l’écoute !")

@client.event
async def on_message(message):
    print(message.content)


client.run("VOTRE_TOKEN")</p>
</details>

## Step 2 first commande:

### 📑 **Description**:

now that wee know how to run a bot and get the message lets do the 1rst commande of our bot and make it answer directly on discord.
to do that wee are gonna need to know in witch chanel the user send to respond to him for that in the message classe wee can use the message.channel.send

```py
message.channel.send("Bonjour !")
```

also wee because event are async to send message wee gonna use await.

```py
@client.event
async def on_message(message):
    await message.channel.send("Bonjour !")

```


### 📌 **Tasks**:

    - make a event when you send !hello in a channel bot answer "Hello human!"
    - make a event when you send !bye in a channel bot answer "Bye human!"

<details> 
<summary>✔️ Result preview</summary>
<p>
@client.event
async def on_message(message):
    if message.content == "!hello":
        await message.channel.send("Hello humain !")
    if message.content == "!bye":
        await message.channel.send("Bye human!")
</p>
</details>

## Step 3 who send you the message:

### 📑 **Description**:

as i have precedentatly say the [message](https://discordpy.readthedocs.io/en/latest/api.html?#message) object have a lots of information like the content previously used. 

for this task wee are gonna see 3 new information:
    -Channel: to give information about the channel where the message is send 
    -Guild: to give information about the discord serveur
    -Author: to give information about who send the message

in object wee also have function like wee use before with the .send() there a lots of thing like that i let you check out what is possible.

### 📌 **Tasks**:

    - the !hello event have to now send back who is sending the masseag like "hello 'user name'!"

<details> 
<summary>✔️ Result preview</summary>
<p>
async def on_message(message):
    if message.content == "!hello":
        await message.channel.send("Hello"+message.Author.name+"!")
</p>
</details>

## Step 4 - style:

### 📑 **Description**:

its cool to send message but its better to do it with style lets see the [embed](https://discordpy.readthedocs.io/en/latest/api.html?#discord.Embed) format r=this allow you to have a title and more. i'm sure you have already saw one.

also in python function can take some Keyword Arguments like for exemple send() take in keyword embed= to send a embed message

```py
em = discord.Embed()
await message.channel.send(embed=em)
```

that the simple use a empty embed now lets do some more complexe message
```py
em = discord.Embed(title="titre", description="desc", colour=0xFF0000, timestamp=message.created_at)
em.add_field(name="a field", value="Youpi", inline=True)
em.add_field(name="a other field", value="o/", inline=True)
em.add_field(name="a new one but not in the same line", value="beca$
1
