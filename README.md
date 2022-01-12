import random
#Cоздаем функции
def passautomat()->str:
	"""Пароль создается машиной
	"""	
	str0=".,:;!_*-+()/#¤%&"
	str1 = '0123456789'
	str2 = 'qwertyuiopasdfghjklzxcvbnm'
	str3 = str2.upper() # 'QWERTYUIOPASDFGHJKLZXCVBNM'
	str4 = str0+str1+str2+str3
	ls = list(str4) # список [".",",",":"...]
	random.shuffle(ls) #перемешаем
# Извлекаем из списка 12 произвольных значений
	psword = ''.join([random.choice(ls) for x in range(12)])
# Пароль готов
	return psword
def paskontroll(psword: str)->bool:
	ls=list(psword)
	for e in ls:
		if e.isdigit(): d=True
		if e.isalpha(): a=True
		if e.isupper(): u=True
		if e.islower():l=True
		if e in list(".,:;!_*-+()/#¤%&"): s=True
	if d==True and a==True and u==True and l==True and s==True:
		t=True
	else:
		t=False
	return t
def koik_kasutajad(users,passwords):
	'''
	'''
	i=0
	for user in users:
		print(user,end='-')
		print(passwords[i])
		i+=1
def autoris(users,passwords):
	'''
	'''
	log=input('Login: ')
	if log not in users:
		print('Sina ei ole registeeritud')
	else:
		pas=input('Parool: ')
		if pas not in passwords:
			print('Vale parool')
		else:
			if users.index(log)==passwords.index(pas):
				print('Tere tulemast')
def reg(users,passwords):
	'''
	'''
	while 1:
		log=input("Kasutajatunnus:")
		if log not in users:
			print("Tunnus soobib")
			break
		else:
			print("See nimi juba on olemas listis")	
	v=input("Arvuti-A või ise-I loob parool")
	if v.upper()=="A":
		pas=passautomat()
		print(f'See on sinu parool:{pas}')
	elif v.upper()=="I":			
		while 1:
			pas=input("Sisesta oma parool")
			tulemus=paskontroll(pas)
			if tulemus==True:
				users.append(log)
				passwords.append(pas)
				break
	return users,passwords
