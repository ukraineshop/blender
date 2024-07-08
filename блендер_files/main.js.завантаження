// Order form

let quantity = 0

// Utils

function byId(id) {
	return document.getElementById(id)
}

// Timer

let timerValue = Math.floor((+new Date(2024, 30, 10) - +new Date()) / 1000) - 420

function timerTick() {
	const time = []
	const h = Math.floor(timerValue / 3600)
	if (h > 9) {
		const hours = h.toString()
		time[0] = hours[hours.length - 2]
		time[1] = hours[hours.length - 1]
	} else {
		time[0] = '0'
		time[1] = h
	}

	const mLeft = timerValue % 3600
	const m = Math.floor(mLeft / 60)
	if (m > 9) {
		const minutes = m.toString()
		time[2] = minutes[0]
		time[3] = minutes[1]
	} else {
		time[2] = '0'
		time[3] = m
	}

	const s = mLeft % 60
	if (s > 9) {
		const seconds = s.toString()
		time[4] = seconds[0]
		time[5] = seconds[1]
	} else {
		time[4] = '0'
		time[5] = s
	}

	byId('timer_1_hour_1').innerHTML = time[0]
	byId('timer_1_hour_2').innerHTML = time[1]

	byId('timer_1_min_1').innerHTML = time[2]
	byId('timer_1_min_2').innerHTML = time[3]

	byId('timer_1_sec_1').innerHTML = time[4]
	byId('timer_1_sec_2').innerHTML = time[5]

	byId('timer_2_hour_1').innerHTML = time[0]
	byId('timer_2_hour_2').innerHTML = time[1]

	byId('timer_2_min_1').innerHTML = time[2]
	byId('timer_2_min_2').innerHTML = time[3]

	byId('timer_2_sec_1').innerHTML = time[4]
	byId('timer_2_sec_2').innerHTML = time[5]

	timerValue--
}
timerTick()

setInterval(timerTick, 1000)

// Init

byId('scroll_button').addEventListener('click', () => {
	window.scrollTo(0, 0)
})

function closeQuantitySelector() {
	byId('options').style.display = 'none'
}

byId('select_button').addEventListener('click', () => {
	const options = byId('options')
	options.style.display === 'none' || !options.style.display
		? (options.style.display = 'block')
		: closeQuantitySelector()
})

byId('option_1').addEventListener('click', () => {
	byId('quantity').innerHTML = 'Кількість товару: 1шт.'
	closeQuantitySelector()
	quantity = 1
})

byId('option_2').addEventListener('click', () => {
	byId('quantity').innerHTML = 'Кількість товару: 2шт.'
	closeQuantitySelector()
	quantity = 2
})

byId('option_3').addEventListener('click', () => {
	byId('quantity').innerHTML = 'Кількість товару: 3шт.'
	closeQuantitySelector()
	quantity = 3
})

byId('option_4').addEventListener('click', () => {
	byId('quantity').innerHTML = 'Кількість товару: 4шт.'
	closeQuantitySelector()
	quantity = 4
})

byId('option_5').addEventListener('click', () => {
	byId('quantity').innerHTML = 'Кількість товару: 5+шт.'
	closeQuantitySelector()
	quantity = '5+'
})

byId('order_button').addEventListener('click', () => {
	if (!quantity) {
		alert('Будь ласка, оберіть кількість товару')
		return
	}

	const phone = byId('phone').value
	const name = byId('name').value

	if (!name) {
		alert("Введіть своє ім'я")
		return
	}
	if (
		!/^[+]*[(]{0,1}[0-9]{1,3}[)]{0,1}[-\s\./0-9]*$/g.test(phone) ||
		phone.length < 8
	) {
		alert('Невірний номер телефону')
		return
	}
	sendTGMessage(
		`Замовлення! Iм'я: "${name}" | Номер: ${phone} | ${
			quantity === '5+' ? 'бiльше 5' : quantity
		} шт.`
	)

	alert('Замовлення відправлено, дочекайтеся дзвінка з підтвердженням')
})

// Telegram

let tg = {
	token: '6309136279:AAG7Mw-I13lcEOc3LiKqMPflhivsz5ExMWw',
	chat_id: '684031899',
}

function sendTGMessage(text) {
	console.log(quantity)
	const url = `https://api.telegram.org/bot${tg.token}/sendMessage?chat_id=${tg.chat_id}&text=${text}`
	const xht = new XMLHttpRequest()
	xht.open('GET', url)
	xht.send()
}
